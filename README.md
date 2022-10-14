# Cookie Banner Project

This is a Vue.js cookie banner component for informing users about cookie use and, if necessary, obtaining consent for cookie use. Accepted or rejected cookie settings are saved in localStorage.

![cookieGIF](https://user-images.githubusercontent.com/14932895/195907532-e33821fd-643f-467b-bfd9-794bf803b7e9.gif)

## [DEMO](https://vue-cookie-comp.netlify.app/)

## Getting Started

To get started you can simply clone this `vue-component-create-eskireaccilar` repository and install the dependencies.

Clone the `vue-component-create-eskireaccilar` repository using git:

```bash
git clone https://github.com/Front-End-Bootcamp/vue-component-create-eskireaccilar.git
cd vue-component-create-eskireaccilar
```

Install dependencies with this command:

```bash
npm install
```

Run the application with this command:

```bash
npm run dev
```

## Usage

### Props

| Prop                   | Type    | Description                                | Default                                                                             |
| ---------------------- | ------- | ------------------------------------------ | ----------------------------------------------------------------------------------- |
| settings               | Array   | Items to show in Cookie Settings Tab       | [{name:'Option-I', status:true}]                                                    |
| title                  | String  | Title to show the top of the banner        | "Title"                                                                             |
| description            | String  | Text to show in the banner for information | We baked some cookies that you have to accept, if you want to enjoy this website... |
| policyText             | String  | Text to show in the Cookie Policy Tab      | Lorem ipsum dolor sit amet consectetur adipisicing elit...                          |
| rejectButtonVisibility | Boolean | Visibility state of the Reject button      | true                                                                                |

### Event Emits

- This component just emits 'buttonClick' event and it returns clicked button's title.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/)
- [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- [TailwindCSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

### Build With:

- [Vue.js](https://vuejs.org/)
- [TailwindCSS](https://tailwindcss.com/)
