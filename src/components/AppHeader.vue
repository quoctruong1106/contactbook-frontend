<template>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
        
    <!-- <nav class="navbar ">  -->
        <a href="/" class="navbar-brand">Ung dung Quan ly danh ba</a>
        
        <div class="mr-auto navbar-nav">
            <li class="nav-item">
                <router-link :to="{name: 'contactbook'}" class="nav-link">
                    Danh ba
                    <i class="fas fa-address-book"></i>
                </router-link>
            </li>

        </div>
    </nav>
</template>