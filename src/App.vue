<template>
    <table class="table table-bordered table-striped table-hover">
        <thead>
        <tr>
            <th class="left-column fw-bold">Lista filmów</th>
            <th class="right-column fw-bold">Opcje</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(video, index) in videos" :key="index">
            <td>{{ video.title }}</td>
            <td>
                <button class="btn btn-outline-danger w-100" @click="deleteVideo(index)">Usuń</button>
            </td>
        </tr>
        </tbody>
        <tfoot>
        <tr>
            <td>
                <input
                    class="form-control"
                    type="text"
                    v-model="videoInput"
                    placeholder="Dopisz nowy film.."
                />
            </td>
            <td>
                <button class="btn btn-success w-100" @click="createVideo">Dodaj</button>
            </td>
        </tr>
        </tfoot>
    </table>
</template>

<script setup>
import { ref } from "vue";

const videoInput = ref("");
const videos = ref([
    { title: "Głupi i głupszy" }
]);

const createVideo = () => {
    if (videoInput.value.trim() !== "") {
        videos.value.push({ title: videoInput.value });
        videoInput.value = "";
    }
};

const deleteVideo = (index) => {
    videos.value.splice(index, 1);
};
</script>

<style scoped>
.left-column {
    width: 100%;
}
</style>
