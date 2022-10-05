# Portfolio Template

This repository is to be use as an example of how to setup a portfolio site using [GitHub Pages](https://pages.github.com/).

## Notable Tech

#### [Parcel JS](https://parceljs.org/)

A quick and easy build tool that you use in declarative way instead of having to write configuration.

#### [React](https://reactjs.org/)

A library for build component-based user interfaces.

#### [TypeScript](https://www.typescriptlang.org/)

Allows your JavaScript to have types, enabling you to catch errors as you write.

#### [SCSS](https://sass-lang.com/documentation/syntax)

Adds chaining, logic, and functions to your CSS which mean less and cleaner styles.

## Getting Started

1. Create a new repository and apply this template. 

    1. Make sure your new repository is public

2. `npm install`

    1. You should install Parcel globally. `npm instal parcel -g`

3. `npm run start`

    1. The above will spin up a local web server with code from `./src`. Hot module replacement / live reloading is enabled by default.

4. Commit your changes then go to the repository on GitHub.

5. Go to the Actions page.

6. Under the workflow sidebar, there should be a `deploy-site` link, go there.

7. Click the `Run workflow` button.

8. After the workflow completes go to the Settings page.

9. Under the sidebar there is a `Pages` section, go there.

10. In Build and deployment section, click the `None` button under the Branch title. Select the `gh-pages` branch.

11. It may take a few minutes but you'll see some messaging and a new section appear on the page tell you that your site is live. Click the `Visit site` button.

12. Your site should have the same content as your local web server.

## Next Steps

If you push your commits directly into `main`, you'll have to manual trigger the workflow to get the site to update (steps 5 - 7). A better way, is to create branches and merge pull requests into `main`. Doing so will result in an automatic deployment.

Deployments are not instant. To check in on the status/progress of your deployment, go to the Code page of your repository. In the sidebar there is an Environments section, you should see `github-pages`. Clicking that link will bring you to the deployment history of your site. An in progress deployment will appear with a yellow rocket ship icon.

## Development

If you want your site to have multiple pages, you may run into some trouble with routing. It is recommend to use the `HashRouter` from `react-router-dom` to achieve a multi-page site. The code below can get you started.

```typescript
import React from 'react';
import { createRoot } from 'react-dom/client';
import { HashRouter as Router, Routes, Route, Navigate } from 'react-router-dom';

const container = document.getElementById('app') as HTMLElement;
const root = createRoot(container);

const PageOnePath = '/';
const PageOne = () => {
  return <div>Page One</div>;
}

const PageOnePath = '/page-two';
const PageTwo = () => {
  return <div>Page Two</div>;
}

const App = () => {
  return (
    <Router>
      <main>
        <Routes>
          <Route path={PageOnePath} element={<PageOne />} />
          <Route path={PageTwoPath} element={<PageTwo />} />
          <Route path="*" element={<Navigate to={PageOnePath} />
        </Routes>
      </main>
    </Router>
  )
};

root.render(<App />);
```