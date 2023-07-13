<script>
export default {
    data() {
        return {
        people: [],
        newPerson: { name: '', age: '', email: '' },
        };
    },
    methods: {
        addPerson() {
        this.people.push({ ...this.newPerson });
        this.newPerson.name = '';
        this.newPerson.age = '';
        this.newPerson.email = '';
        },
        removePerson(index) {
        this.people.splice(index, 1);
        },
    },
};
</script>

<template>
    <div class="flex flex-col py-2 ">
      <div class="-my-2 sm:-mx-6 lg:-mx-8">
        <div class="py-2 align-middle items-center inline-block sm:px-6 lg:px-8">
          <div class="shadow overflow-hidden rounded-3xl bg-gray-800 text-white border-gray-200">
            <table class="table-fixed divide-y divide-gray-700">
              <thead class="bg-gray-700">
                <tr>
                  <th
                    scope="col"
                    class="px-4 py-3 text-left text-xs font-medium uppercase tracking-wider"
                  >
                    Name
                  </th>
                  <th
                    scope="col"
                    class="px-4 py-3 text-left text-xs font-medium uppercase tracking-wider"
                  >
                    Age
                  </th>
                  <th
                    scope="col"
                    class="px-4 py-3 text-left text-xs font-medium uppercase tracking-wider"
                  >
                    Email
                  </th>
                  <th
                    scope="col"
                    class="px-4 py-3 text-right text-xs font-medium uppercase tracking-wider"
                  >
                    <button
                      @click="addPerson"
                      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-3 rounded"
                    >
                      +
                    </button>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-700">
                <tr
                  v-for="(person, index) in people"
                  :key="index"
                >
                  <td class="px-4 py-4 whitespace-nowrap">
                    <input v-model="person.name" class="border rounded-lg px-3 py-2 w-full bg-gray-800 text-white" />
                  </td>
                  <td class="px-4 py-4 whitespace-nowrap">
                    <input v-model="person.age" class="border rounded-lg px-3 py-2 w-full bg-gray-800 text-white" />
                  </td>
                  <td class="px-4 py-4 whitespace-nowrap">
                    <input v-model="person.email" class="border rounded-lg px-3 py-2 w-full bg-gray-800 text-white" />
                  </td>
                  <td class="px-4 py-4 whitespace-nowrap text-right">
                    <button
                      @click="removePerson(index)"
                      class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-3 rounded"
                    >
                      -
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </template>

  <style>
  input[type='text'],
  input[type='email'] {
    border: 1px solid #4a5568;
    padding:0.5rem;
    border-radius: 0.5rem;
  }
  </style>