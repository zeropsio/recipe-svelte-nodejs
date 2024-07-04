<script>
import Code from './+code.svelte';
const importyaml = `project:
  name: recipe-solidjs
  tags:
    - zerops-recipe

services:
  - hostname: app
    type: nodejs@20
    enableSubdomainAccess: true
    buildFromGit: https://github.com/zeropsio/recipe-solidjs-nodejs`.trim();

const zeropsyaml = `zerops:
  - setup: app
    build:
      base: nodejs@20
      buildCommands:
        - pnpm i
        - pnpm run build
      deployFiles:
        - build
        - package.json
        - node_modules
    run:
      base: nodejs@20
      ports:
        - port: 3000
          httpSupport: true
      start: pnpm start`.trim();
</script>

    <div>
      <div class="flex justify-center">
        <p class="text-center mx-auto">Deploying will import the following structure (zerops-project-import.yml)<br/>
        and use following (zerops.yml) instructions to build and deploy your app:</p>
      </div>
      <div class="grid grid-cols md:grid-cols-2 font-light gap-5 md:gap-10 pt-4">
        <div class="flex flex-col gap-5">
          <Code fileLink="https://github.com/zeropsio/recipe-solid-nodejs/blob/main/zerops-project-import.yml" file="zerops-project-import.yml" code={importyaml} />
          <div
          class="flex flex-col py-10 h-[260px] rounded-md gap-5 px-10 bg-[#242424]"
        >
          <a
            href="https://github.com/zeropsio/recipe-svelte-nodejs"
            target="_blank"
            class="primarybutton rounded-full text-center text-md duration-300 hover:no-underline"
            >Recipe Source Code</a>
          <a
            href="https://discord.com/invite/WDvCZ54"
            target="_blank"
            class="discordbutton rounded-full text-center text-md duration-300 hover:no-underline"
            >Discord</a>
          <a
            href="https://docs.zerops.io"
            target="_blank"
            class="zeropsbutton rounded-full text-center text-md duration-300 hover:no-underline"
            >Documentation</a>
        </div>
        </div>
        <div class="flex flex-col">
          <Code fileLink="https://github.com/zeropsio/recipe-solid-nodejs/blob/main/zerops.yml" file="zerops.yml" code={zeropsyaml} />
        </div>
      </div>
    </div>
