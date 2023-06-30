<script>
export default{
    name:'HeaderComp',
}

</script>


<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">LOGO</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse justify-content-around" id="navbarNav">
        <ul class="navbar-nav p-2">
            <li class="nav-item">
            <RouterLink class="nav-link active" aria-current="page" :to="{name: 'home' }">Home</RouterLink>
            </li>
            <li class="nav-item">
            <RouterLink class="nav-link" :to="{ name:'projects' }">Projects</RouterLink>
            </li>        
        </ul>
        <ul class="navbar-nav p-2">
            <a href=""><li class="nav-item me-1"><i class="fa-brands fa-linkedin" style="color: #51441f;"></i></li></a>
            <a href=""><li class="nav-item me-1"><i class="fa-brands fa-instagram" style="color: #51441f;"></i></li></a>
            <a href="mailto:giorgioprizzi@gmail.com"><li class="nav-item me-1"><i class="fa-regular fa-envelope" style="color: #51441f;"></i></li></a>
            <a href="https://github.com/Giorgiopri22"><li class="nav-item me-1"><i class="fa-brands fa-square-github" style="color: #51441f;"></i></li></a>
        </ul>
        </div>
    </div>
</nav>
</template>

<style lang="scss" scoped>


</style>