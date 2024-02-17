<template>
    <div class="h-screen flex justify-center bg-white font-mono bg-gradient-to-tr from-cyan-300 via-blue-300 to-purple-400">
        <div class="h-2/3 w-1/3 bg-slate-100 m-auto rounded-3xl shadow-slate-500 shadow-xl">
            <div class="flex flex-col gap-10 items-center justify-center p-8 h-full ">
                <div class="header text-center">
                    <h1 class="text-xl font-bold">
                        Welcome to TODO List!
                    </h1>
                    <h3>Place your ToDo List and Keep it <span>Organized!</span></h3>
                </div>
                <div class="form text-left">
                    <form action="" class="flex flex-col gap-4 ">
                        <div>
                            <label for="username">Username</label><br>
                            <input type="text" id="username" name="username" placeholder="Username"
                                class="rounded-lg px-2 shadow-md"><br>
                        </div>
                        <div>
                            <label for="password">Password</label><br>
                            <input type="text" id="password" name="password" placeholder="Password"
                                class="rounded-lg px-2 shadow-md"><br>
                        </div>
                        <button
                            class="cursor-pointer bg-white w-full rounded-lg shadow-md hover:bg-slate-200">Login</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>
  