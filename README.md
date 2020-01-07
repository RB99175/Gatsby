# Gatsby

[Gatsby](https://www.gatsbyjs.org/) is a open source framework powered by React.js that allows developer to build highly optimized front-end applications.

## Why use Gatsby
- Blazing Fast (passes all lighthouse tests out of the box)
- SEO built in
- Easy to use
- Built off of React
- AMAZING DOCUMENTATION (probably the best part)

## Let's Get Started

- `npm i -g gatsby-cli`
- `gatsby new [your app name]`
- `cd [your app name]`
- `gatsby develop`

## Difference between gatsby develop and gatsby build
In simple terms gatsby develop launches a hot-reloading development enviroment for building your app (think npm start).
Gatsby build will create a highly optimized version of your site by generating static HTML and JavaScript bundles.

## Check pre-built files
Take 15min to take a look at the files gatsby has generated for you and answer these questions in comparison to react:
- What looks familiar?
- What is the path of data?
- What looks different? 
- How are things rendered on the page?

## Let's Build Something
- Remove all uneeded files that were generated from gatsby new command
- Inside pages folder add `About.js` file
- Inside that file make changes to reflect the following 
```
import React from "react"
import { Link } from "gatsby"

const SecondPage = () => (
  <main>
    <Link to="/">Home</Link>

    <h1>About me</h1>
  </main>
)

export default SecondPage
```

Next lets go back to index and add a Link to our new page

Index.js
```
import React, { Component } from "react"
import { Link } from "gatsby"

class IndexPage extends Component {
  constructor(props) {
    super(props)
}

  render() {
    return (
      <main>
        <Link to="/about/">About</Link>
      </main>
    )
  }
}

export default IndexPage
```

Now take a look at your application in the browser, What Happend?

Gatsby has handled all the routing for us!

## Re-create Dad Jokes
