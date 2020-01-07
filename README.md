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
First create a joke.js file inside the components folder.

Inside of that file create a joke component that takes a setup and punchline as props
```
import React from "react"


export default props => (
    <section>
    <p>{props.setup}</p>
    <h3>{props.punchline}</h3>
  </section>
)
```

Lets add this component to our index.js

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
        <Joke punchline={this.state.punchline} setup={this.state.setup} />
      </main>
    )
  }
}

export default IndexPage
```

Now we need to handle our api call and set up some state variables to render the joke element with the needed data

```
import React, { Component } from "react"
import { Link } from "gatsby"
import Joke from "../components/joke"

class IndexPage extends Component {
  constructor(props) {
    super(props)

    this.state = {
      setup: "",
      punchline: "",
    }

    this.getJoke = this.getJoke.bind(this)
  }
  componentDidMount() {
    this.getJoke()
  }

  getJoke() {
    fetch("https://official-joke-api.appspot.com/random_joke")
      .then(res => {
        return res.json()
      })
      .then(resJson => {
        console.log(resJson)
        this.setState({setup: resJson.setup, punchline: resJson.punchline })
      })

  }

  render() {
    return (
      <main>
        <Link to="/about/">About</Link>
       
        <Joke punchline={this.state.punchline} setup={this.state.setup} />
        <button style={button} onClick={this.getJoke}>click for new joke</button>
      </main>
    )
  }
}

export default IndexPage


 ```
 
 We now have the basic structure and some text rendering on the page
 
 ## Styling in Gatsby
 
 There are a million ways to style gatsby including using layout components, standered CSS files and a million others.

- [intro to styling](https://www.gatsbyjs.org/tutorial/part-two/)
- [more advanced styling](https://www.gatsbyjs.org/docs/styling/)

 please take a look at these amazing resources for a depper dive into styling in gatsby.
 
 For our purposes lets handle our styling within the javascript file by creating css objects like this.
 
 ```
 const button = {
  padding: '20px',
  fontSize: '20px',
  backgroundColor: 'black',
  color: 'white',
  margin: '20px auto',
}
```
Your final index.js file should look like this:
```
 import React, { Component } from "react"
import { Link } from "gatsby"
import Joke from "../components/joke"


const button = {
  padding: '20px',
  fontSize: '20px',
  backgroundColor: 'black',
  color: 'white',
  margin: '20px auto',
}

const body = {
  textAlign: 'center'
}


class IndexPage extends Component {
  constructor(props) {
    super(props)

    this.state = {
      setup: "",
      punchline: "",
    }

    this.getJoke = this.getJoke.bind(this)
  }
  componentDidMount() {
    this.getJoke()
  }

  getJoke() {
    fetch("https://official-joke-api.appspot.com/random_joke")
      .then(res => {
        return res.json()
      })
      .then(resJson => {
        console.log(resJson)
        this.setState({setup: resJson.setup, punchline: resJson.punchline })
      })

  }

  render() {
    return (
      <main style={body}>
        <Link to="/about/">About</Link>

        <Joke punchline={this.state.punchline} setup={this.state.setup} />
        <button style={button} onClick={this.getJoke}>click for new joke</button>
      </main>
    )
  }
}

export default IndexPage
```

## Further resources

- [gatsby and ecommerce](https://www.gatsbyjs.org/tutorial/ecommerce-tutorial/)
- [User Authentication](https://www.gatsbyjs.org/tutorial/authentication-tutorial/)

 
