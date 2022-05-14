Following [this guide](https://www.smashingmagazine.com/2020/07/desktop-apps-electron-vue-javascript/)

Starting:

```
Opened git-bash prompt in windows terminal
cd /d/git
mkdir vue
cd vue
yarn global add @vue/cli
yarn global add electron
vue create news-app
// here I selected the default Vue 3 config and yarn as package manager
cd news-app
```

They use axios, so added that:

```
yarn add axios
```

Adding axios instance for global config, create 'src/plugins' folder and add axios.js:

```js
import axios from "axios";
let baseURL = `https://newsapi.org/v2`;
let apiKey = process.env.VUE_APP_APIKEY;
const instance = axios.create({
    baseURL: baseURL,
    timeout: 30000,
    headers: {
        "X-Api-Key": apiKey,
    },
});
export default instance;
```

To get the API key I signed up [here](https://newsapi.org/register).
To use it I created a `.env` file in the root directory:

```
VUE_APP_APIKEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

And added `.env` to the `.gitignore` file so it won't be stored in source
control.  For anyone who downloads this repo to use the service they
will have to create the `.env` file themselves.

And adding `electron-builder`:

```
vue add electron-builder
```
