<template>
    <Head title="New Project" />
  
    <AuthenticatedLayout>
      <template #header>
        <h2 class="font-semibold text-xl text-gray-800 leading-tight">Create Projects</h2>
      </template>
  
      <div class="py-12">
        <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
          <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
            <form @submit.prevent="submit" class="p-2 m-2">
              <div >
                <InputLabel for="name" value="Skill" />
                <select v-model="form.skill_id" id="skill_id" name="skill_id" class="mt-1 w-full rounded text-base ">
                  <option v-for="skill in skills" :key="skill.id" :value="skill.id"> {{ skill.name }}</option>
                </select>
                <InputError class="mt-2" :message="form.errors.skill_id" />
              </div>
            <div>
                <InputLabel for="name" value="Name" />

                <TextInput
                    id="name"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.name"
                    autocomplete="name"
                />

                <InputError class="mt-2" :message="form.errors.name" />
            </div>

            <div>
                <InputLabel for="project_url" value="URL" />

                <TextInput
                    id="project_url"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.project_url"
                    autocomplete="project_url"
                />

                <InputError class="mt-2" :message="form.errors.project_url" />
            </div>
            <div>
                <InputLabel for="image" value="Image" />

                <TextInput
                    id="image"
                    type="file"
                    class="mt-1 block w-full"
                    @input="form.image=$event.target.files[0]"
                />

                <InputError class="mt-2" :message="form.errors.image" />
            </div>   
            
            <div class="flex items-center justify-end mt-4">
                

                <PrimaryButton class="ms-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Submit
                </PrimaryButton>
            </div>
        </form>
            
          </div>
        </div>
      </div>
    </AuthenticatedLayout>
  </template>
  <script setup>
  import { Head,useForm } from "@inertiajs/vue3";
  import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
  import InputError from '@/Components/InputError.vue';
  import InputLabel from '@/Components/InputLabel.vue';
  import PrimaryButton from '@/Components/PrimaryButton.vue';
  import TextInput from '@/Components/TextInput.vue';
  defineProps({
    skills:Array
  });
  const form = useForm({
    name:'',
    image:null,
    skill_id:'',
    project_url:''
  });
  const submit =()=>{
    form.post(route('projects.store'));
  }
  </script>