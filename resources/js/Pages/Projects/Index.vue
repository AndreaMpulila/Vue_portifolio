<template>
  <Head title="Projects" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Projects
      </h2>
    </template>

    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
          <div class="flex justify-end m-2 p-2">
            <Link
              :href="route('projects.create')"
              class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md"
              >Add Project</Link
            >
          </div>
          <div class="relative overflow-x-auto">
            <table class="w-full text-sm text-left rtl:text-right">
              <thead
                class="text-xs text-gray-700 uppercase dark:border-grey-700"
              >
                <tr>
                  <th scope="col" class="px-6 py-3">Id</th>
                  <th scope="col" class="px-6 py-3">Image</th>
                  <th>Skill</th>
                  <th scope="col" class="px-6 py-3">Name</th>
                  <th scope="col" class="px-6 py-3">Project Link</th>
                  <th scope="col" class="px-6 py-3"></th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="project in projects.data"
                  :key="project.id"
                  class="bg-white border-b dark:border-grey-900"
                >
                  <td scope="row" class="px-6 py-4 font-medium">
                    {{ project.id }}
                  </td>
                  <td class="px-6 py-4">
                    <img
                      :src="project.image"
                      class="h-20 h-20 rounded-full"
                      alt=""
                    />
                  </td>
                  <td class="px-6 py-4">
                    {{ project.skill }}
                  </td>
                  <td class="px-6 py-4">
                    {{ project.name }}
                  </td>
                  <td class="px-6 py-4">
                    <a :href="project.project_url" target="_blank"> Link</a>
                  </td>
                  <td class="px-6 py-4">
                    <Link
                      :href="route('projects.edit', project.id)"
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
                      :href="route('projects.destroy', project.id)"
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
  </AuthenticatedLayout>
</template>
<script setup>
import { Head, Link } from "@inertiajs/vue3";
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
defineProps({
  projects: Object,
});
</script>