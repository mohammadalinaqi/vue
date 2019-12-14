<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
      <input type="text" v-model= "name">
      <p>Name is : {{ name }}</p>
      <p>Age is : {{ age }}</p>
      <button @click="changeName">Change My Name</button>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail
                  :myName="name"
                  @nameWasReset="name = $event"
                  :resetFn ="resetName"
                  :userAge="age"></app-user-detail>

            </div>
            <div class="col-xs-12 col-sm-6">
                <app-user-edit
                  :userAge = "age"
                  @ageWasEdited = "age = $event"
                ></app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
      data (){
        return{
          name: 'Ali',
          age: 23
        };
      },
      methods:{
        changeName(){
          this.name = 'Mohammad'
        },
        resetName(){
          this.name = 'Ali';
        }
      },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
