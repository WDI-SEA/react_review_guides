# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

## Review Guide: React Router
Below, you'll find key terms and key code snippets - all covering the basics of browser history mechanics and React Router.

### Key Terms & Definitions


* **Browser History Mechanics**
  - Operations designed to track history as users move between different pages.
  - For example, JavaScript functions of `window.history.back()` and `window.history.forward()`
  - HTML5 introduced `.pushState()` and `.replaceState()` for Single-Page Applications, called modern browser history mechanics.

* **`exact`**
  - A special attribute when defining paths
  - The `exact` attribute means the component associated with the route will only be shown if users are at exactly that URL path.
  - Otherwise, partial matches will also be shown. For example, when someone navigates to `/courses` they will actually see two components, because `/` is a partial match for `/courses`, if no `exact` keyword is used.
  - Example usage: `<Route exact path="/" component={HomePage} />`

* **`Link`**
  - A component that creates `<a>` tags and automatically integrates modern HTML5 browser history mechanics for the single-page application.
  - `link` has one attribute, `to`
    - `to` designates what path to navigate to when the user clicks the link.
    - This takes a *path* for a value, **not** a component.
  - For example, `<Link to="/procedures">See Our Procedures</Link>`

* **Path**
  - The path of a URL is everything after the domain name.
  - For example, if the URL is `https://myPage.com/pandas`, the path is `/pandas`
  - The `/` path is a special path called the root. It loads the home page. For example, `https://myPage.com/`

* **React Router**
  - A third party library that makes it easy for programmers to route URLs.
  - It dynamically loads different components on the same page.
  - It automatically manages browser history when the user navigates between content.
  - You install React Router with `npm install --save react-router-dom`
  - React Router is configured using Route components.

* **Route Components**
  - Components provided by the React Router library.
  - Each `<Route>`component has two pieces:
    - `path` - This defines the URL path that leads to the component.
    - `component` - This defines what component users will see when they navigate to the path.
  - All together, a Route component looks like this: `<Route path="/courses" component={CoursesPage} />`

* **Single-Page Applications (SPAs)**
  - Websites that serve only one web page and then change the content of that page dynamically, without refreshing or sending the user to a separate page.

* **URL Routing**
  - Defines what content is displayed when someone visits a certain a URL.


### Key Code Snippets

**Complete component file using `<Route>` and `<Link>`**.
- This assumes the referenced components are correctly imported.

```js
class App extends Component {
  render() {
    return (
      <Router>
        <div>
          <nav>
            <Link to="/">Go to Home Page</Link>{' '}
            <Link to="/procedures">See Our Procedures</Link>{' '}
            <Link to="/contact">Contact Us!</Link>
          </nav>
          <Route exact path="/" component={Home} />
          <Route path="/procedures" component={Procedures} />
          <Route path="/contact" component={Contact} />
        </div>
      </Router>
    );
  }
}

export default App;
```


**Example of using `props` within a Route**

```js
<Route path="/blog" component={
    () => (<Blog title={post.title}
              author={post.author}
              body={post.body}
              comments={post.comments} />
)}/>
```
