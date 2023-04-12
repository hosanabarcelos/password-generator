<template>
    <div>
        <div class="main__container">
            <img src="@/assets/banner.png">
            <GeneratePasswordForm />
        </div>
    </div>
</template>

<script>
import GeneratePasswordForm from '@/components/GeneratePasswordForm.vue';

export default {
  components: {
    GeneratePasswordForm
  }
}

</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
    font-family: 'Roboto', sans-serif;
    font-size: x-large;
}
.main__container {
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #201E30;
    gap: 100px;
    margin: 0;
    padding: 0;
}
img {
    width: 320px;
    padding-top: 114px;
}
</style>
