# bank-app
This web app was developed for creating a list of bank credit proposition and calculating monthly payment for a bank credit
## Project setup
```
Project realized on Vue.js.
```First of all, you should built in all modules, using npm install, and then run project

## About the Project
```
First step in project is filling in the list of banks. With the help of form of inputs you can make a list of banks with relevant parameters. After submiting the form, data will be stored in localStorage.
Below the input form will be the list of saved banks.
Every bank item has three buttons: "select", "edit", and "delete"
"Edit" and "delete" buttons make changes in lis of saved banks.
"Select" button is used for select appropriate bank for calculating monthly payments for credit.
There are two inputs below the bank list: "initial loan", and "down payment".
To get result, the bank should be selected(using "select" button), and enter data in  "initial loan", and "down payment" inputs. After pushing "calculate" button, the app will check if input values correspond selected bank and will show the result "Your monthly payment".
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
### Author
Viktor Sobolevskyi

### Contributing
Any contributions you make are greatly appreciated.
Sorry for simple design, I didn`t have enought time for it.


