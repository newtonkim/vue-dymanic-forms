<template>
<div class="flex mt-5" style="width: 100%;">
    <div class="w-3/12">

    </div>
    <div class="w-6/12 p-5">
        <div class="shadow-md p-5 rounded-md">

        <div class="form">
            <h1 class="text-white">Create an Event</h1>
        
            <form @submit.prevent="sendForm"> 
        
                <BaseSelect
                    :options="categories"
                    v-model="event.category" 
                     label="Select a category"
                />
              
        
              <h3>Name and Description of your Event</h3>
        
              <BaseInput
                v-model="event.title"
                label="Title"
                type="text"
              />
              
             <br/>
              <BaseInput
                v-model="event.description"
                label="Description"
                type="text"
                
              />
              
              <h3 class="mt-5">Where is your Event ?</h3>
        
        
              <BaseInput
                v-model="event.location"
                label="Location"
                type="text"
              />
        
              <h3 class="my-5">Are pets allowed ?</h3>
        
              <div>
                <BaseRadioGroup
                    v-model="event.pets"
                    name="pets" 
                    :options="petOptions"
                />
              
              </div>
        
              <h3 class="my-5">Extras</h3>
              <div>
                <BaseCheckbox
                    v-model="event.extras.catering" 
                    label="Catering"
                />
              </div>
        
              <div>
                <BaseCheckbox
                    v-model="event.extras.music" 
                    label="Live Band"
                />
              </div>
              <button class="button-fill-gradient mt-5 bg-blue-500 text-white w-full p-2 rounded-md" type="submit">Submit</button>
            </form>
          </div>
          </div>
    </div>
    <div class="w-3/12">
    </div>

</div>


</template>

<script>
import axios from 'axios';
import BaseInput from "../components/BaseInput.vue";
import BaseSelect from "../components/BaseSelect.vue";
import BaseCheckbox from "../components/BaseCheckbox.vue";
import BaseRadioGroup from "../components/BaseRadioGroup.vue";
export default {
    components: {
        BaseInput,
        BaseSelect,
        BaseCheckbox,
        BaseRadioGroup
  },
  data() {
    return {
      categories: [
        "sustainability",
        "nature",
        "animal welfare",
        "housing", 
        "education",
        "food",
        "community",
        ],
        
    
      event: {
        category: "",
        title: "",
        description: "",
        location: "",
        pests: 1,
        extras: {
          catering: false,
          music: false,
        }
        },
        petOptions: [
            { label: 'Yes', value: 1 },
            { label: 'No', value: 0 }
      ]
    }
    },
    methods: {
        sendForm() {
            axios.post('https://my-json-server.typicode.com/newtonkim/Events-app/events',
            this.event
            ).then((response) => {
                console.log('reponse',response.data);
            }).catch((error) => {
                console.log('error',error.data);
            }) 
        }
    }
    }

</script>
  



<style>

</style>