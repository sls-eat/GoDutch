<script>
export default {
    data() {
        return {
            people: [],
            newPerson: { name: '', pay: 0 },
        };
    },
    methods: {
        addPerson() {
            this.people.push({ ...this.newPerson });
            this.newPerson.name = '';
            this.newPerson.pay = 0;
        },
        removePerson(index) {
            this.people.splice(index, 1);
        },
    },
};
</script>

<template>
    <div class="
        absolute top-1/3 
        flex flex-col align-middle items-center
        h-1/2 w-1/2 rounded-3xl bg-slate-800
        shadow-xl shadow-indigo-500/50 
        transition hover:shadow-emerald-500/50 duration-50"
    >
        <table class="
            table-fixed divide-y divide-gray-700 w-full
            text-2xl
            overflow-auto
        ">
            <thead>
                <tr>
                    <th class="py-4 font-medium">
                        飯腳 LUNCHMATE
                    </th>
                    <th class="py-4 font-medium">
                        價錢 PRICE
                    </th>
                    <th class="py-4 pr-4 text-xs text-right">
                        <button @click="addPerson"
                        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-3 rounded">
                            +
                        </button>
                  </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(person, index) in people">
                    <td class="py-4">
                        <input v-model="person.name" class="ml-4 text-center" />
                    </td>
                    <td class="py-4">
                        <input v-model="person.pay" class="ml-4 text-center" />
                    </td>
                    <td class="py-4 pr-4 text-xs text-right">
                        <button @click="removePerson(index)"
                            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-3 rounded">
                            -
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>