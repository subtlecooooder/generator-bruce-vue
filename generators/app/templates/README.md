<!--
 * @Descripttion: 
 * @Author: fjy
 * @Date: 2020-05-28 15:06:09
 * @LastEditors: fjy
 * @LastEditTime: 2020-05-28 15:07:06
--> 
# <%= name%>

```bash
# clone the project
git clone https://tanzhiguo@bitbucket.org/vlove/visitant.git

# install dependency
npm install

# develop
npm run dev
```

This will automatically open http://localhost:9527.

## Build

```bash
# build for test environment
npm run build:sit

# build for production environment
npm run build:prod
```

## Advanced

```bash
# --report to build with bundle size analytics
npm run build:prod --report

package.json 中的buildVersion 每次打包需要加1

# --generate a bundle size analytics. default: bundle-report.html
npm run build:prod --generate_report

# --preview to start a server in local to preview
npm run build:prod --preview

# lint code
npm run lint

# auto fix
npm run lint -- --fix
```

## Background

```
From vue-element-admin
commit : 6234db924e572e3106ccdf7450621af29486f753
```
