# The unofficial P11 online form (confirmation of sending the letter) generator for Polish Post

|Video presentation <Br />of the project|Screenshot <br />of the project|
|--|--|
|[![Video presentation of the project](https://s08.pl/git/img/post/post-youtube.png)](https://www.youtube.com/watch?v=x7ZSG-QgDtk)|[![Screenshot of the project](https://s08.pl/git/img/post/post-screen.png)](https://unofficial-p11-form-generator.netlify.app)|

I wrote this generator to make it easier for Poczta Polska customers to prepare the confirmation print on their own.
The app is an unofficial private project. This generator works 100% in the client's browser. It allows you to:

- preparation of any number of prints theP11 form
- export and import of data in json format
- printing of documents to pdf (a4)

This generator is based on the pixelperfect approach. The form template in the application corresponds to the paper form template. The form is prepared with attention to detail.

![Screen shot of the project](https://s08.pl/git/img/post/pdf.png)


## Live site url 

https://unofficial-p11-form-generator.netlify.app - I invite you check, go ahead and click :)

## What do we have here?

I built the application on **Vue.js** 2 (Vue CLI, Single File Components). I work with **reusable components**, I use the concept of **slots** and vue **transistion**. I was using the **html-to-pdf-js package** to generate printouts. Each document is printed on a separate page. Style is **pure scss** without ony frameworks (my code with bem). The application scores high in the lighthouse test:
![Screen shot of the project](https://s08.pl/git/img/post/hiscrore.png)


## Roadmap
 - [ ] perfection in terms of accessibility (although it's already pretty good :))
 - [ ] adding google sheets export and import options
 - [ ] additional printing options
 - [ ] I'm considering about refactor on vue 3


## Project setup
Project setup

    yarn install

Compiles and hot-reloads for development

    yarn serve

Compiles and minifies for production

    yarn build

Lints and fixes files

    yarn lint

