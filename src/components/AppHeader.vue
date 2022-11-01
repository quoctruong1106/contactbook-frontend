<template>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
        
    <!-- <nav class="navbar ">  -->
        <a href="/" class="navbar-brand">Ứng dụng Quản lý Danh bạ</a>
        
        <div class="mr-auto navbar-nav">
            <li class="nav-item">
                <router-link :to="{name: 'contactbook'}" class="nav-link">
                    Danh bạ
                    <i class="fas fa-address-book"></i>
                </router-link>
            </li>

        </div>
    </nav>
</template>