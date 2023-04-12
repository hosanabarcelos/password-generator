<template>
    <div class="form__container">
        <h1>* * * * *</h1>
        <main>
            <form>
                <div class="form__generated-password">
                    <input
                        v-model="generatedPassword"
                        :min="min"
                        :max="max"
                    >
                </div>
                <div class="form__range">
                    <input
                        type="range"
                        :min="min"
                        :max="max"
                        v-model="passwordLength"
                    >
                    <input
                        v-model="passwordLength"
                        :min="min"
                        :max="max"
                    >
                </div>
                <div class="form__checkbox">
                    <input
                        v-model="uppercase"
                        type="checkbox"
                    />
                    <label>Letras maiúsculas</label>
                </div>
                <div class="form__checkbox">
                    <input
                        type="checkbox"
                        v-model="numbers"
                    />
                    <label>Números</label>
                </div>
                <div class="form__checkbox">
                    <input
                        type="checkbox"
                        v-model="symbols"
                    />
                    <label>Caracteres especiais</label>
                </div>
        </form>
        </main>
    </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const generatedPassword = ref('')
const min = 6;
const max = 30;
const passwordLength = ref(min);
const uppercase = ref(false);
const numbers = ref(false);
const symbols = ref(false);


const lowercaseChars = 'abcdefghijklmnopqrstuvwxyz';
const uppercaseChars = 'ABCDEFGHIJKLMNOPQRSTUVXYZ';
const numbersChars = '0123456789';
const symbolsChars = '!@#$%^&*()_+-={}[]|:;"<>,.?/';

const generateRandomPassword = () => {
    generatedPassword.value = '';
    let baseChars = lowercaseChars;

    if(uppercase.value) {
        baseChars += uppercaseChars;
    }

    if(numbers.value) {
        baseChars += numbersChars;
    }

    if(symbols.value) {
        baseChars += symbolsChars;
    }

    for (let i = 0; i < passwordLength.value; i++) {
        const randomPassword = Math.floor(Math.random() * baseChars.length)
        generatedPassword.value += baseChars[randomPassword]
    }
}
generateRandomPassword();

watch([passwordLength, uppercase, numbers, symbols], () => {
    generateRandomPassword();
});
</script>

<style scoped>
.form__container {
    display: flex;
    align-items: center;
    flex-direction: column;
    color: #DCDCDC;
    font-weight: 600;
}
.form__range, .form__checkbox {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 6px;
}
.form__range input {
    width: 18%;
    font-size: 18px;
    background-color: transparent;
}
.form__checkbox {
    margin-bottom: 8px;
}
h1 {
    font-size: 52px;
}
main {
    width: 80%;
    padding: 50px;
    border-radius: 12px;
    display: flex;
    flex-direction: column;
    gap: 15px;
    background-color: #2F2E41;
}

label {
    font-weight: 400;
    font-size: 16px;
    color: #DCDCDC;
    margin-left: 4px;
}

main > div {
    display: flex;
    align-items: center;
    gap: 10px;
}

input {
    width: 100%;
    padding: 10px;
    outline: none;
    border-radius: 6px;
    accent-color: #000000;
    background: #3F3D56;
    color: #FFF;
    border: none;
}

input[type=checkbox] {
    width: 18px;
    height: 18px;
}

input[type=range] {
    width: 90%;
}

button {
    width: 100%;
    border: none;
    cursor: pointer;
    border-radius: 8px;
    padding: 16px;
    background: #000000;
    color: #DCDCDC;
    font-size: 14px;
    font-weight: 600;
    text-transform: uppercase;
    margin-top: 14px;
}
</style>
