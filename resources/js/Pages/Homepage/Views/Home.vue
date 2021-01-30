<template>
    <div class="max-w-6xl mx-auto pb-32">
        <div class="flex flex-col">
            <div class="h-32">
                <logo class="h-32 w-full object-contain"></logo>
            </div>
            <h1 class="docu-title">Laravel Starter Package</h1>
            <h2 class="docu-subtitle">Implementation documentation</h2>

            <h3 class="docu-caption">Installation</h3>
            <pre class="docu-code">
composer global remove laravel/installer
composer global require laravel/installer
laravel --version</pre
            >
            <div class="docu-text">
                laravel/framework had version 8.12 on 15.01.2021
            </div>

            <h3 class="docu-caption">Database</h3>
            <div>
                The following database values were entered in .env:
            </div>
            <pre class="docu-code">
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravelstarterpackage-test
DB_USERNAME=root
DB_PASSWORD=12345678</pre
            >

            <h3 class="docu-caption">Configuration</h3>
            <div>
                Open the app.php file in the config directory.<br />
                Change the following values:<br />
                'timezone' => 'Europe/Berlin',<br />
                'locale' => 'de',<br />
                'fallback_locale' => 'de',<br />
                'faker_locale' => 'de',<br />
            </div>

            <h3 class="docu-caption">
                Installation of vue, less and tailwindcss
            </h3>
            <pre class="docu-code">
npm install
npm install vue --save-dev
npm install vue-template-compiler --save-dev
npm install less --save-dev
npm install less-loader --save-dev
npm install tailwindcss --save-dev
npm install laravel-mix-tailwind --save-dev
npm install autoprefixer --save-dev</pre
            >

            <div>
                Remove the css directory under resources. Create the new
                directory less under resources/js.<br />
                For this new directory create the file app.less with the
                following content:<br />
            </div>
            <pre class="docu-code">
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";</pre
            >
            <div>Now we create the file tailwind.config.js</div>
            <pre class="docu-code">npx tailwindcss init</pre>

            <div>Add the following to tailwind.config.js:</div>
            <pre class="docu-code">
future: {
    removeDeprecatedGapUtilities: true,
    purgeLayersByDefault: true
},
purge: ["./resources/views/**/*.blade.php", "./resources/js/**/*.vue"],</pre
            >

            <div>
                Now we customize the webpack.mix.js file:
            </div>

            <pre class="docu-code">
const mix = require("laravel-mix");
const tailwindcss = require("tailwindcss");
require("laravel-mix-tailwind");
mix.js("resources/js/app.js", "public/js/app.js")
    .less("resources/less/app.less", "public/css/app.css")
    .options({
        postCss: [tailwindcss("./tailwind.config.js")],
    });</pre
            >

            <h3 class="docu-caption">Last Steps</h3>
            <div>
                Remove laravel-mix:
            </div>
            <pre class="docu-code">
npm uninstall laravel-mix --save-dev
npm install laravel-mix@5.0.9 --save-dev</pre
            >

            <div>
                Now make the following modifications in package.json:
            </div>
            <pre class="docu-code">
"scripts": {
    "dev": "npm run development",
    "development": "cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
    "watch": "npm run development -- --watch",
    "watch-poll": "npm run watch -- --watch-poll",
    "hot": "cross-env NODE_ENV=development node_modules/webpack-dev-server/bin/webpack-dev-server.js --inline --hot --disable-host-check --config=node_modules/laravel-mix/setup/webpack.config.js",
    "prod": "npm run production",
    "production": "cross-env NODE_ENV=production node_modules/webpack/bin/webpack.js --no-progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js"
},</pre
            >

            <div>And still install:</div>
            <pre class="docu-code">npm install cross-env --save-dev</pre>

            <div>Now run the following command:</div>
            <pre class="docu-code">
npm run watch
valet link</pre
            >

            <div>
                Then call the following address in the browser:
                <br />
                <a href="http://laravelstarterpackage.test" class="docu-link"
                    >http://laravelstarterpackage.test</a
                >
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
