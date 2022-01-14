<template>
  <div class="container">
    <h3>Todo App</h3>
    <hr />
   <InputSection />
   <ListSection  />
  </div>
</template>

<script>
import axios from "axios";
import InputSection from "@/components/InputSection";
import ListSection from "@/components/ListSection";
export default {
  data() {
    return {
      provideData: {
      itemsList: [],
      }
    };
  },
  mounted() {
    axios.get("http://localhost:3000/items").then(items_response => {
      console.log("items_response :>> ", items_response);
      this.provideData.itemsList = items_response.data || [];
      console.log("this.itemsList :>> ", this.provideData.itemsList);
            console.log(this.itemCount)

    });
  },
  methods: {
    onSave(e) {
      const saveObject = {
        title: e.target.value,
        created_at: new Date(),
        completed: false
      };
      axios.post("http://localhost:3000/items", saveObject).then(save_response => {
        console.log(save_response);
        this.provideData.itemsList.push(save_response.data);
        e.target.value = "";
        e.target.focus();
      });
    },
    onDelete(item) {
      axios.delete(`http://localhost:3000/items/${item.id}`).then(delete_response => {
        console.log(delete_response);
        this.provideData.itemsList = this.provideData.itemsList.filter(i => i.id !== item.id);
      });
    }
  },

   
     components: {
      InputSection,
      ListSection
    },
    provide(){
      return{
        onSave: this.onSave,
        onDelete: this.onDelete,
        provideData: this.provideData
        };
  }
};
</script>