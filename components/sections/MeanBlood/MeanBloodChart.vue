<script lang="ts" setup>
import type { IMeanBlood } from '~/types';
import moment from "moment";
import { Line } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  PointElement,
  LinearScale,
  TimeScale,
} from "chart.js";
import "chartjs-adapter-date-fns";

interface RangeOption {
  name: string;
  value: number;
}

interface IProps {
  data: IMeanBlood[]
}

const props = defineProps<IProps>()

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  LineElement,
  PointElement,
  LinearScale,
  TimeScale
);

const rangeOptions = ref<RangeOption[]>([
  { name: "Last 12 Months", value: 12 },
  { name: "Last 6 Months", value: 6 },
  { name: "Last 3 Months", value: 3 },
]);

const selectedRange = ref<number>(12);
const chartData = ref({});
const chartOptions = ref({});

const calculateDateRange = (months: number): { start: moment.Moment; end: moment.Moment } => {
  const now = moment();

  const endDate = now.clone();

  const startDate = now.clone().subtract(months - 1, "months").startOf("month");

  return { start: startDate, end: endDate };
};

const formatDate = (date: moment.Moment): string => moment(date).format("ddd, YYYY/MM/DD");

const formattedDateRange = computed((): string => {
  const range = calculateDateRange(selectedRange.value);
  return `${formatDate(range.start)} to ${formatDate(range.end)}`;
});

const updateChartAndRange = (): void => {
  const range = calculateDateRange(selectedRange.value);

  const filteredData = props.data.filter((item) => {
    const itemDate = moment(item.date);
    return itemDate.isBetween(range.start, range.end, "day", "[]");
  });

  const dataset = filteredData.map((item) => ({
    x: moment(item.date).toDate(),
    y: item.value,
  }));


  chartData.value = {
    datasets: [
      {
        label: "Values",
        data: dataset,
        borderColor: "#0F7A8A",
        backgroundColor: "#0F7A8A",
        fill: false,
        tension: 0,
        pointRadius: 5,
        pointHoverRadius: 7,
      },
    ],
  };

  chartOptions.value = {
    responsive: true,
    plugins: {
      legend: {
        display: false,
      },
    },
    scales: {
      x: {
        type: "time",
        time: {
          unit: "month",
        },
        title: {
          display: false,
        },
      },
      y: {
        ticks: {
          stepSize: Math.ceil(100 / selectedRange.value),
        },
        title: {
          display: false,
        },
        beginAtZero: true,
      },
    },
  };
};

updateChartAndRange();

const emit = defineEmits(['close'])
</script>

<template>
  <div class="">
    <div class="flex justify-between mb-2">
      <div>
        <p class="text-xs text-gray-500">Abhishek</p>
        <h4 class="font-semibold">Mean Blood</h4>
      </div>
      <div class="flex gap-2 items-center">
        <USelect v-model="selectedRange" @change="updateChartAndRange" :options="rangeOptions"
          option-attribute="name" />
        <UButton icon="ph:x" size="sm" color="gray" square @click.prevent="emit('close')" />
      </div>
    </div>
    <p class="text-end text-xs text-gray-500 mb-2">{{ formattedDateRange }}</p>
    <div class="mb-4">
      <Line :data="chartData" :options="chartOptions" />
    </div>
  </div>
</template>
