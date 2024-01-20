# my_project

# creating project using vue CLI

vue create projectName

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# modifiers

A suffix you can add to either the v-on directive or v- model directive to add some functionality inline within the template it helps to worite cleaner code
like trim,number,lazy,prevent,key

# Bonus Directives

v-once - Render the corresponding HTML element only once. On subsequent re-renders,trated as static content and skiped

v-pre - not to compile html element it is render as it is

# ways to display data in the UI

1 Static Html 2. Text Interpolation 3. Simple explression 4. Methods 5. Computed Property

Computed Properties :

bound to template like data propertires
they are used for composing new data from existing sources
They are highly performant as they cached calculation which only update when dependencies changes
