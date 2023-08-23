### Step 1. Install and Configure 

1. Run vite with vanilla and ts
```bash
$ npm create vite@latest guess-the-word --template vanilla-ts
```
```bash
$ yarn create vite guess-the-word --template vanilla-ts
```
```bash
$ pnpm create vite guess-the-word --template vanilla-ts
```
2. Install rune-sdk and vite plugin
```bash
# yarn
yarn add --dev vite-plugin-rune rune-games-sdk

# npm
npm install --dev vite-plugin-rune rune-games-sdk
```

3. Create a `vite.config.ts` file and place this code inside it 

```js
// vite.config.ts
import { defineConfig } from "vite"
import rune from "vite-plugin-rune"

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [rune({ logicPath: "./src/logic.ts" })],
})
```
4. Create file logic.ts inside src directory and place this code

```ts
import type { RuneClient,  } from "rune-games-sdk/multiplayer"

export interface GameState {}

export type GameActions = {

}

declare global {
    const Rune:RuneClient<GameState,GameActions>
}
```
5. import it in the html before the main.ts file
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + TS</title>
  </head>
  <body>
    <div id="app"></div>
     <script type="module" src="/src/logic.ts"></script> <!-- add file here-->
    <script type="module" src="/src/main.ts"></script>
  </body>
</html>
```


6. add Rune.initClient inside main.ts and render the game

