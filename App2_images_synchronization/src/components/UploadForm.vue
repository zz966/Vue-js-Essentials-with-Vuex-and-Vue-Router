<template>
<div>
     <h2>upload images to your imgur account</h2>
     <div class="dropper">
     
      <input type='file' @change="uplaodImages($event.target.files)" multiple accept="image/*"/>
      <span> Drag files here
      </span>
  </div>
</div>
  
</template>

<script>
import { mapActions } from 'vuex'
export default {
    name:'UploadForm',
    methods:mapActions(["uplaodImages"]),
}
</script>

<style scoped>
.dropper{
    height: 30vh;
    border:2px dashed black;
    border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.dropper:hover{
    background-color: #eee;
}
input{
    width: 100%;
    height: 30vh;
    position: absolute;
    opacity: 0;
}
h2{
    text-align: center;
}
</style>