<template>
    <div class="max-w-6xl mx-auto">
        <div class="flex flex-col">
            <div class="h-32">
                <logo class="h-32 w-full object-contain"></logo>
            </div>
            <h1 class="mt-8 text-5xl">Laravel Starter Package</h1>
            <h2 class="mt-8 text-3xl">Implementation documentation</h2>

            <h3 class="mt-8 text-2xl">Installation</h3>
            <code class="bg-gray-100 my-2 p-2">
                composer global remove laravel/installer
                <br />
                composer global require laravel/installer
                <br />
                laravel --version
            </code>
            <div>
                laravel/framework had version 8.12 on 15.01.2021
            </div>

            <h3 class="mt-8 text-2xl">Database</h3>
            <div>
                The following database values were entered in .env:
                <br />
                DB_CONNECTION=mysql<br />
                DB_HOST=127.0.0.1<br />
                DB_PORT=3306<br />
                DB_DATABASE=laravelstarterpackage-test<br />
                DB_USERNAME=root<br />
                DB_PASSWORD=12345678<br />
            </div>

            <h3 class="mt-8 text-2xl">Configuration</h3>
            <div>
                Open the app.php file in the config directory.<br />
                Change the following values:<br />
                'timezone' => 'Europe/Berlin',<br />
                'locale' => 'de',<br />
                'fallback_locale' => 'de',<br />
                'faker_locale' => 'de',<br />
            </div>

            <h3 class="mt-8 text-2xl">
                Installation of vue, less and tailwindcss
            </h3>
            <code class="bg-gray-100 my-2 p-2">
                npm install<br />
                npm install vue --save-dev<br />
                npm install vue-template-compiler --save-dev<br />
                npm install less --save-dev<br />
                npm install less-loader --save-dev<br />
                npm install tailwindcss --save-dev<br />
                npm install laravel-mix-tailwind --save-dev<br />
                npm install autoprefixer --save-dev<br />
            </code>

            <div>
                Remove the css directory under resources. Create the new
                directory less under resources/js.<br />
                For this new directory create the file app.less with the
                following content:<br />
            </div>
            <code class="bg-gray-100 my-2 p-2">
                @import "tailwindcss/base"; <br />
                @import "tailwindcss/components"; <br />
                @import "tailwindcss/utilities"; <br />
            </code>
            <div>Now we create the file tailwind.config.js</div>
            <code class="bg-gray-100 my-2 p-2">
                npx tailwindcss init
            </code>

            <div>Add the following to tailwind.config.js:</div>
            <code class="bg-gray-100 my-2 p-2">
                purge: ["./resources/views/**/*.blade.php",
                "./resources/js/**/*.vue"],
            </code>

            Now we customize the webpack.mix.js file:

            <code class="bg-gray-100 my-2 p-2">
                const mix = require("laravel-mix"); const tailwindcss =
                require("tailwindcss"); require("laravel-mix-tailwind");
                mix.js("resources/js/app.js", "public/js/app.js")
                .less("resources/less/app.less", "public/css/app.css")
                .options({ postCss: [tailwindcss("./tailwind.config.js")], });
            </code>

            <h3 class="mt-8 text-2xl">Last Steps</h3>

            <div>
                Now make the following modifications in package.json:
            </div>
            <code class="bg-gray-100 my-2 p-2">
                "scripts": {<br />
                "dev": "npm run development",<br />
                "development": "cross-env NODE_ENV=development
                node_modules/webpack/bin/webpack.js --progress --hide-modules
                --config=node_modules/laravel-mix/setup/webpack.config.js",<br />
                "watch": "npm run development -- --watch",<br />
                "watch-poll": "npm run watch -- --watch-poll",<br />
                "hot": "cross-env NODE_ENV=development
                node_modules/webpack-dev-server/bin/webpack-dev-server.js
                --inline --hot --disable-host-check
                --config=node_modules/laravel-mix/setup/webpack.config.js",<br />
                "prod": "npm run production",<br />
                "production": "cross-env NODE_ENV=production
                node_modules/webpack/bin/webpack.js --no-progress --hide-modules
                --config=node_modules/laravel-mix/setup/webpack.config.js"<br />
                },<br />
            </code>

            <div>And still install:</div>
            <code class="bg-gray-100 my-2 p-2">
                npm install cross-env --save-dev
            </code>

            <div>Now run the following command:</div>
            <code class="bg-gray-100 my-2 p-2">
                npm run watch
                <br />
                valet link
            </code>

            <div>
                Then call the following address in the browser:
                <br />
                http://laravelstarterpackage.test/
            </div>
        </div>
    </div>
</template>

<script>
import Logo from "@/js/Pages/Shared/Logo/Logo";
//
export default {
    name: "Home",
    //
    components: {
        Logo
    }
};
</script>
