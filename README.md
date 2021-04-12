# Next Layout Template

A project starter that allows for multiple layouts. In this case, one dashboard template with header, footer and sidebar, and a second template with header and content only. More layout templates can easily be added.

## How to use

## How to create from scratch

All instructions will assume the use of `yarn`. If using `npm`, install `create-next-app` and use to create your project.

In addition, I have left out the use of `git`, but I strongly suggest you do use some form of version control.

### Initial Setup

- `> yarn create next-app next-layout-template`

- `cd next-layout-template`

- Remove the api folder: `rm -rf pages/api`
- Remove stock styles: `rm styles/Home.module.css`
- Alter `styles/globals.css` as desired
- Replace `pages/index.js` content with this MVP content

  ```
  const Home = () => {
      return <div>Home</div>
  }

  export default Home
  ```

  Then run `yarn dev` and see `Home` in your browser at `localhost:3000`

### Create a global layout

- create a components and inside a layout component directory : `mkdir -p components/layout`
- add an index file for your layout component, and a scss module
  - `touch components/layout/index.js components/layout/layout.module.scss`
  - we will deal with any styling later
- add your base layout component

  ```
  const Layout = (props) => {
      return (
          <div>
              <h2>In Layout</h2>
              {props.children}
          </div>
      )
  }

  export default Layout
  ```

- now import your layout into `pages/_app.js`

  ```
  import Layout from "../components/layout"

  import "../styles/globals.css"

  function MyApp({ Component, pageProps }) {
      return (
          <Layout>
              <Component {...pageProps} />
          </Layout>
      )
  }

  export default MyApp
  ```

  At this point you should see both your layout `h2` and your home page title, so you can see that your layout will be applied to all pages.
