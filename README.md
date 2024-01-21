# Natural History Museum task

A task to display data for a museum

REQUIREMENTS

1. Cards displaying highlights from the space partners' API should have a different color branding from those in the museum's own data.

2. While in this case the card only needs to work for the Space page, the card component needs to be done in such a way that it would be easily expandable to the other pages. The museum could have X number of pages and they could continually be adding new ones. As a developer, you don't know what those pages might be.

2.1.    Each page has a special badge in the top right corner of the card. This badge is different on every page, and could be an image, or some styled html elements, or a Font Awesome icon. The Space page has an image of a star. The Dinosaur page has a Font Awesome icon inside a circle. The Oceans page has two Font Awesome icons, a wave and a fish together. And so on...

2.2     The data on the different pages (Space, Dinosaurs...) have commonalities but also differences. All highlights have a name, image, date they were posted, a brief description, and perhaps associated news. But all pages also have extra unique data. For example, on the space page, some highlights also include a link to a quiz on the topic. On the dinosaur card, we have a "Period" key to indicate when that dinosaur lived. On the Wildlife page, we have several additional keys: "Location", "Species", and "Endangered status".

3. Each card should have a "Refresh image" button which, when clicked, will replace that card's current image with a new image fetched from an API.

3.1     When implementing this functionality, assume that you have already received the new image from the API. E.g. const newImage = await getNewImage(); where you do not need to implement the getNewImage() function.

3.2     You only need to implement the code which will replace the current image with the new image for the relevant card.

4. The cards should be arranged in order of date created, with the most recent first.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

Move into app directory

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
