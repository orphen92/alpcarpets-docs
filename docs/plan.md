# Architecture du projet Angular

Voici un diagramme illustrant la structure de l'application h24.

Retrouver la documentation de chaque page en cliquant sur les noeuds

``` mermaid
stateDiagram-v2
    Homepage: <a href="../pages/home/">Homepage</a>
    notFound: <a href="../pages/404/">404</a>
    aboutUs: <a href="../pages/about-us/">About us</a>
    allProject: <a href="../pages/all-project/">All project</a>
    collectionList: <a href="../pages/collection-list/">List Collection</a>
    collection: <a href="../pages/collection/">Collection Detail</a>
    contact: <a href="../pages/contact/">Contact Us</a>
    collectionFocus: <a href="../pages/focus-collection/">Collection Focus</a>
    privacy: <a href="../pages/privacy/">Privacy</a>
    productDetail: <a href="../pages/product-detail/">Product Detail</a>
    project: <a href="../pages/project/">Project</a>
    loginRegister: <a href="../pages/signup-register/">Signup/Register</a>
    textures: <a href="../pages/textures/">Textures</a>
    tools: <a href="../pages/tools/">Tools</a>

    Homepage --> textures
    Homepage --> allProject
    Homepage --> aboutUs
    Homepage --> tools
    Homepage --> contact
    Homepage --> loginRegister
    Homepage --> collectionList
    Homepage --> collectionFocus
    Homepage --> notFound
    Homepage --> privacy
    collectionList --> collection
    allProject --> project
    project --> productDetail
    tools --> productDetail
```
