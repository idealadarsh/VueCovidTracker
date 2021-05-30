<template>
    <div class="grid md:grid-cols-3 gap-4">
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numberWithCommas(stats.NewConfirmed) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numberWithCommas(stats.TotalConfirmed) }}
            </div>
        </div>

        <div class="shadow-md bg-red-100 p-10 text-center rounded">
            <h3 class="text-3xl text-red-900 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numberWithCommas(stats.NewDeaths) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numberWithCommas(stats.TotalDeaths) }}
            </div>
        </div>

        <div class="shadow-md bg-green-100 p-10 text-center rounded">
            <h3 class="text-3xl text-green-900 font-bold mb-4">Recovered</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numberWithCommas(stats.NewRecovered) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numberWithCommas(stats.TotalRecovered) }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DataBoxes',
    props: ['stats'],
    methods: {
        numberWithCommas(n) {
            let x = n.toString()
            let lastThree = x.substring(x.length-3)
            let otherNumbers = x.substring(0,x.length-3)
            if(otherNumbers != '') lastThree = ',' + lastThree;
            let res = otherNumbers.replace(/\B(?=(\d{2})+(?!\d))/g, ",") + lastThree;
            return res
        }
    }
}
</script>