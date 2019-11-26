This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `yarn build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify

### Instalações de confiigurações padrão 

Instalações Sucrase + Nodemon;

yarn add sucrase nodemon -D

É necessário configurar o pakage.json e criar o arquivo nodemon.json assim como o lauch.json para o debug automatico

package.json: "scripts":{ "dev": "nodemon src/server.js", "dev:debug":"nodemon --inspect src/server.js" },

nodemon.json: { "execMap":{ "js": "node -r sucrase/register" } }

launch.json: { // Use IntelliSense to learn about possible attributes. // Hover to view descriptions of existing attributes. // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387 "version": "0.2.0", "configurations": [ { "type": "node", "request": "attach", "name": "Launch Program", "restart": true, "protocol": "inspector" } ] }

ESLint + Prettier + EditorConfig;

yarn add eslint -D yarn eslint --init { Escolhas: yarn run v1.19.1 $ /home/hudson/projetosJS/GynPoint/node_modules/.bin/eslint --init ? How would you like to use ESLint? To check syntax, find problems, and en force code style ? What type of modules does your project use? JavaScript modules (import/e xport) ? Which framework does your project use? None of these ? Does your project use TypeScript? Yes ? Where does your code run? Node ? How would you like to define a style for your project? Use a popular sty le guide ? Which style guide do you want to follow? Airbnb (https://github.com/airb nb/javascript) ? What format do you want your config file to be in? JavaScript Checking peerDependencies of eslint-config-airbnb-base@latest The config that you've selected requires the following dependencies:

@typescript-eslint/eslint-plugin@latest eslint-config-airbnb-base@latest eslint@^5.16.0 || ^6.1.0 eslint-plugin-import@^2.18.2 @typescript-eslint/parser@latest ? Would you like to install them now with npm? Yes

} Após executar remover package.lock.json e rodar o comando yarn na pasta

configurar o arquivo eslintrc.js module.exports = { "env": { "es6": true, "node": true }, "extends": [ "airbnb-base" ], "globals": { "Atomics": "readonly", "SharedArrayBuffer": "readonly" }, "parserOptions": { "ecmaVersion": 2018, "sourceType": "module" }, "rules": { "class-methods-use-this": "off", "no-param-reassign": "off", "camelcase": "off", "no-unused-vars": ["error", { "argsIgnorePattern": "next" }], }, };

Prettier: yarn add prettier eslint-config-prettier eslint-plugin-prettier -D

alterar o eslintrc.js "extends": [ "airbnb-base", "prettier" ], "plugins": ['prettier'], rules: {
     'prettier/prettier': 'error',
     'react/jsx-filename-extension': [
        'warn',
        { extensions: ['.jsx', '.js'] }
     ],
     'import/prefer-default-export': 'off',
      'react/state-in-constructor': ['warn', 'never']
  },

criar e configurar .prettierrc { "singleQuote": true, "trailingComma": "es5" }

EditorConfig após instalar a extensão clicar com o botão ditero na rais e ir na opção generate .editorConfig, e colocar o seguinte conteudo: root = true

[*] indent_style = space indent_size = 3 charset = utf-8 trim_trailing_whitespace = true insert_final_newline = true

Sequelize (Utilize PostgreSQL ou MySQL);

instalar sequelize yarn add sequelize yarn add sequelize-cli -D

criar o arquivo .sequelizerc com o conteudo abaixo(é necessário criar a estrutura de pastas): const { resolve } = require('path');

module.exports = { config: resolve(__dirname, 'src', 'config', 'database.js'), 'models-path': resolve(__dirname, 'src', 'app', 'models'), 'migrations-path': resolve(__dirname, 'src', 'database', 'migrations'), 'seeders-path': resolve(__dirname, 'src', 'database', 'seeds') }

para bancos postgres é necessário instalar as dependencias pg e pg-hstore

yarn add pg pg-hstore

migrations: yarn sequelize migration:create --name=create-users

apos definição doas campos da tabela no arquivo de migrations, rodar o comando: yarn sequelize db:migrate

yarn sequelize db:seed:all

Subir instancia do MongoDB no Docker: docker run --name mongobarber -p 27017:27017 -d -t mongo testar localhost:27017


yarn add react-router-dom 
