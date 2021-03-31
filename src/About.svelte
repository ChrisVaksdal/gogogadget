<script lang="ts">

    // Calculate age:
    let today: Date = new Date();
    let birthday: Date = new Date(1999, 3, 19);
    let age: number = (today.getFullYear() - birthday.getFullYear());

</script>
<section class="container about">
    <h1 class="title has-text-centered section-title">About Me</h1>
    <div class="columns is-12 is-multiline">
        I'm <span class="name">Chris Vaksdal.</span> <br>
        I am a {age} year old 3rd year student at the Norwegian University of Science and Technology,
        currently studying for a Masters Degree in Electronic Systems Design (<a href="https://www.ntnu.no/studier/mtelsys">Elsys</a>).

    </div>
</section>

<style>
    .name{
        font-weight: 600;
    }
</style>