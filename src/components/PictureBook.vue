<template>
    <body>
        <div class="wrapper">
            <div class="container">
                <input type="radio" name="slide" id="c1" checked>
                <label for="c1" class="card">
                    <div class="row">
                        <div class="icon">1</div>
                        <div class="description">
                            <h4>Picture 1</h4>
                            <!-- pass openModal an argument with the description for the picture -->
                            <button class="details" @click="openModal">...</button>
                        </div>
                    </div>
                </label>
                <input type="radio" name="slide" id="c2">
                <label for="c2" class="card">
                    <div class="row">
                        <div class="icon">2</div>
                        <div class="description">
                            <h4>Picture 2</h4>
                            <button class="details" @click="openModal">...</button>
                        </div>
                    </div>
                </label>
                <input type="radio" name="slide" id="c3">
                <label for="c3" class="card">
                    <div class="row">
                        <div class="icon">3</div>
                        <div class="description">
                            <h4>Picture 3</h4>
                            <button class="details" @click="openModal">...</button>
                        </div>
                    </div>
                </label>
                <input type="radio" name="slide" id="c4">
                <label for="c4" class="card">
                    <div class="row">
                        <div class="icon">4</div>
                        <div class="description">
                            <h4>Picture 4</h4>
                            <button class="details" @click="openModal">...</button>
                        </div>
                    </div>
                </label>
                <input type="radio" name="slide" id="c5">
                <label for="c5" class="card">
                    <div class="row">
                        <div class="icon">5</div>
                        <div class="description">
                            <h4>Picture 5</h4>
                            <button class="details" @click="openModal">...</button>
                        </div>
                    </div>
                </label>
            </div>
        </div>
        <!-- here you need to pass the PictureDetails component the pictureDescription as a prop -->
        <PictureDetails :pictureDescription="pictureDescription" :isOpen="isModalOpened" @modal-close="closeModal" name="first-modal">
            <template #details>{{ pictureDescription }}</template>
        </PictureDetails>
    </body>
</template>

<!-- the idea here is that I need to pass the information about the particular picture
    that I'm trying to see details for to the modal using props -->

<script setup>
import { ref } from "vue";
import PictureDetails from "./PictureDetails.vue";

const isModalOpened = ref(false);

//picture description
const pictureDescription = ref("Graduation day at Tech Elevator! .NET FOR LIFE");

const pictures = ref[
    {
        id: 1,
        title: 'pic 1 title',
        description: 'picture 1'
    },
    {
        id: 2,
        title: 'pic 2 title',
        description: 'picture 2'
    },
    {
        id: 3,
        title: 'pic 3 title',
        description: 'picture 3'
    },
    {
        id: 4,
        title: 'pic 4 title',
        description: 'picture 4'
    },
    {
        id: 5,
        title: 'pic 5 title',
        description: 'picture 5'
    }
];

const openModal = () => {
    isModalOpened.value = true;
    //change another property here in the script to reflect the correct description
    //pictureDescription = string;
};

const closeModal = () => {
    isModalOpened.value = false;
}
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, Helvetica, sans-serif;
}

body {
    background-color: #eeeeea;
}

.wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}


.container {
    height: 400px;
    display: flex;
    flex-wrap: nowrap;
    justify-content: start;
}

.card {
    width: 60px;
    border-radius: .75rem;
    background-size: cover;
    cursor: pointer;
    overflow: hidden;
    border-radius: 2rem;
    margin: 0 5px;
    display: flex;
    align-items: flex-end;
    transition: .6s cubic-bezier(.28, -0.03, 0, .99);
    box-shadow: 0px 10px 30px -5px rgba(0, 0, 0, 0.8);
}

.card>.row {
    color: white;
    display: flex;
    flex-wrap: nowrap;
}

.card>.row>.icon {
    color: #223;
    background: white;
    border-radius: 50%;
    width: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 15px;
}

.card>.row>.description {
    display: flex;
    justify-content: center;
    flex-direction: column;
    overflow: hidden;
    height: 80px;
    width: 520px;
    opacity: 0;
    transform: translateY(30px);
    transition-delay: .3s;
    transition: all .3s ease;
}

.description {
    color: #b0b0ba;
    padding-top: 5px;
}

.description h4 {
    text-transform: uppercase;
}

.details {
    color: #223;
    background: white;
    font-weight: bolder;
    border-radius: 50%;
    width: 40px;
    display: flex;
    justify-content: center;
    align-self: end;
    margin-right: 50px;
    margin-bottom: 20px;
}

input {
    display: none;
}

input:checked+label {
    width: 600px;
}

input:checked+label .description {
    opacity: 1 !important;
    transform: translateY(0) !important;
}

.card[for="c1"] {
    background-image: url('../assets/IMG_1935.JPG');
}

.card[for="c2"] {
    background-image: url('../assets/IMG_1898.jpg');
}

.card[for="c3"] {
    background-image: url('../assets/IMG_1861.JPG');
}

.card[for="c4"] {
    background-image: url('../assets/IMG_1944.jpg');
}

.card[for="c5"] {
    background-image: url('../assets/ThankYouTE.jpg');
}</style>