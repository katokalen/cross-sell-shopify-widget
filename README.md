# Cross-sell Shopify Widget

Minimal Online Store 2.0 theme with the essentials to run and extend.

- Production url: htttps://pact-fbc9diqo.myshopify.com
- Dev URLS will be preview urls from Shopify
- Using the "Horizon" theme (see link below for documentation)

## Requirements

- Node.js >= 20.10 (I'm using v24.6.0)
- Shopify CLI >= v4.7.0 https://shopify.dev/docs/api/shopify-cli

## Local setup

- Clone this repo
- Make sure Shopify CLI tool is installed
- While in the /horizon subfolder, run the command `shopify theme pull`. This pulls all the latest live theme code.
- See if there are any changed files you don't expect, if there are, commit them back into the repo into origin/main
- If there are not any changed files, create a feature branch and work as normal
- `shopify theme dev` will create a local dev environment at http://127.0.0.1:9292
- You can also use the dev command to generate a preview link and a link to the theme editor for the development theme.

## NOTE: Content .json files

To safely push everything EXCEPT .json files, run the following command:
`shopify theme push --ignore "*.json"`

To only pull the latest .json content from the shopify theme, run the following command:
`shopify theme pull --only "*.json"`

If you're worried about any of your changes deleting files, you can also pass the `--nodelete` flag like so:
`shopify theme push --nodelete --ignore "*.json"`
`shopify theme pull --nodelete --only "*.json"`

## Contributing, feature branch rules

1. Work from a separate feature branch, prepended to match Jira ticket numbers. Eg: `XY-123-feature-name`
2. Run `shopify theme pull` on the live theme and commit any changed code back into origin/main before starting your work in your feature branch.
3. Make a copy of the live theme in Shopify and rename it to reference the ticket ID. There is where your in progress work should be pushed to.
4. Work on your code changes, committing them to your feature branch
5. When your feature is ready for testing, open a PR in github to merge into origin/main, and then run the `shopify theme push --theme XXXXXX --nodelete` command to push your feature branch code into a your testing theme you created in step 3.
6. Update the Jira ticket with your branch name, then assign to QA or fellow Team Member for sanity check
7. When the work is ready to be deployed, merge your PR and then run `shopify theme push` to push into the live theme `shopify theme push --theme NAMEOFTHEME --nodelete`

## Deployment processes

NOTE: We do not have any CI/CD set up in Github Actions, or in DeployHQ. Everything is done through the Shopify CLI.

When the work is ready to be deployed, merge your PR and then run `shopify theme push` to push into the live theme

More info on flow here:
https://shopify.dev/docs/storefronts/themes/getting-started/customize#step-5-share-your-changes