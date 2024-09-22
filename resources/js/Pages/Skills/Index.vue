<template>
  <Head title="Skills" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">Skills</h2>
    </template>

    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
          <div class="flex justify-end m-2 p-2">
            <Link
              :href="route('skills.create')"
              class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md"
              >Add Skill
            </Link>
          </div>
          <div class="p-6 text-gray-900">
            <div class="relative overflow-x-auto">
              <table class="w-full text-sm text-left rtl:text-right">
                <thead
                  class="text-xs text-gray-700 uppercase dark:border-grey-700"
                >
                  <tr>
                    <th scope="col" class="px-6 py-3">Id</th>
                    <th scope="col" class="px-6 py-3">Name</th>
                    <th scope="col" class="px-6 py-3">Image</th>
                    <th scope="col" class="px-6 py-3"></th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="skill in skills.data"
                    :key="skill.id"
                    class="bg-white border-b dark:border-grey-900"
                  >
                    <th scope="row" class="px-6 py-4 font-medium">
                      {{ skill.id }}
                    </th>
                    <td class="px-6 py-4">
                      {{ skill.name }}
                    </td>
                    <td class="px-6 py-4">
                      <img
                        :src="skill.image"
                        class="h-20 h-20 rounded-full"
                        alt=""
                      />
                    </td>
                    <td class="px-6 py-4">
                      <Link
                        :href="route('skills.edit', skill.id)"
                        as="button"
                        type="button"
                        px-4
                        py-2
                        bg-indigo-500
                        hover:bg-black-700
                        text-white
                        rounded-md
                        class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md"
                      >
                        Edit</Link
                      >
                      <Link
                        :href="route('skills.destroy', skill.id)"
                        method="delete"
                        as="button"
                        type="button"
                        px-4
                        py-2
                        bg-indigo-500
                        hover:bg-black-700
                        text-white
                        rounded-md
                        class="px-4 py-2 bg-red-500 hover:bg-red-700 text-white rounded-md m-1"
                      >
                        Delete</Link
                      >
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>
<script setup>
import { Head, Link } from "@inertiajs/vue3";
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
defineProps({
  skills: Object,
});
</script>