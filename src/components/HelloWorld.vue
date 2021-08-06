<template>
    <div class="hello">
        <apexchart
            type="rangeBar"
            height="200"
            :options="chartOptions"
            :series="series"></apexchart>
    </div>
</template>

<script>
    import VueApexCharts from 'vue-apexcharts';
    //import seriesJson from '../assets/series.json'

    export default {
        name: 'HelloWorld',
        components: {
            apexchart: VueApexCharts
        },
        data: function () {
            return {
                series: [
                    {
                        name: '경기대학교',
                        data: [
                            {
                                x: ' ',
                                y: [
                                    new Date(2016, 3, 21).getTime(),
                                    new Date(2021, 2, 4).getTime()
                                ]
                            }
                        ]
                    }, {
                        name: '경기대학교',
                        data: [
                            {
                                x: ' ',
                                y: [
                                    new Date(2021, 3, 21).getTime(),
                                    new Date(2024, 2, 4).getTime()
                                ]
                            }
                        ]
                    }, {
                        name: '경기대학교',
                        data: [
                            {
                                x: ' ',
                                y: [
                                    new Date(2024, 3, 21).getTime(),
                                    new Date(2026, 2, 4).getTime()
                                ]
                            }
                        ]
                    }, {
                        name: '경기대학교',
                        data: [
                            {
                                x: ' ',
                                y: [
                                    new Date(2026, 3, 21).getTime(),
                                    new Date(2036, 2, 4).getTime()
                                ]
                            }
                        ]
                    }
                ],
                chartOptions: {
                    chart: {
                        height: 350,
                        type: 'rangeBar'
                    },
                    plotOptions: {
                        bar: {
                            horizontal: true,
                            barHeight: '50%',
                            rangeBarGroupRows: true
                        }
                    },
                    colors: [
                        "#008FFB",
                        "#00E396",
                        "#FEB019",
                        "#FF4560",
                        "#775DD0",
                        "#3F51B5",
                        "#546E7A",
                        "#D4526E",
                        "#8D5B4C",
                        "#F86624",
                        "#D7263D",
                        "#1B998B",
                        "#2E294E",
                        "#F46036",
                        "#E2C044"
                    ],
                    fill: {
                        type: 'solid'
                    },
                    xaxis: {
                        type: 'datetime'
                    },
                    yaxis: {},
                    legend: {
                        position: 'top'
                    }
                },
                annotations: {
                    points: [
                        {
                            x: 150,
                            y: new Date(2026, 3, 21).getTime(),
                            marker: {
                                size: 6,
                                fillColor: "#fff",
                                strokeColor: "#2698FF",
                                radius: 2
                            },
                            label: {
                                borderColor: "#FF4560",
                                offsetY: 0,
                                style: {
                                    color: "#fff",
                                    background: "#FF4560"
                                },

                                text: "Point Annotation (XY)"
                            }
                        }
                    ]
                }
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

    div.apexcharts-toolbar {
        display: none !important;
    }
</style>