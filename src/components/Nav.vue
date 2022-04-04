<script setup>
import {useRouter} from "vue-router";
import useAuth from "../composable/useAuth";
const {isAuthenticated, logout} = useAuth();

const router = useRouter();

const loggingOut = () => {
    logout();
    router.push("/");
}

</script>




<template>
   <div class="bg-red-400 text-black">
        <div class="container mx-auto flex items-center italic justify-between ">
            <h1 class="tracking-tighter text-3xl font-semibold">
                Sneaker<span class="font-normal">Shop</span>
                </h1>
            <nav>
                <ul class="flex space-x-4">
                    <router-link to="/">
                    <li class="py-8 px-4  hover:cursor-pointer hover:bg-black hover:text-red-300">
                        Home
                        </li></router-link>
                     <router-link to="/about">   
                    <li class="py-8 px-4 hover:cursor-pointer hover:bg-black hover:text-red-300">About</li>
                    </router-link>
                    <router-link v-if="!isAuthenticated" to="/login">
                    <li class="py-8 px-4 hover:cursor-pointer hover:bg-black hover:text-red-300">Login</li>
                    </router-link>

                    <div v-else class="flex">
                     <router-link  to="/secret">
                    <li class="py-8 px-4 hover:cursor-pointer hover:bg-black hover:text-red-400">Secret</li>
                    </router-link>


                     <button  @click="loggingOut">
                    <li class="py-8 px-4 hover:cursor-pointer hover:bg-gray-500 hover:text-pink-300">Logout</li>
                    </button>
                    </div>
                    
                </ul>

            </nav>
            
        </div>
        </div>
    <h1 class="text-center text-xl py-6">Welcome to Manny's Sneaker Shop!</h1>
</template>