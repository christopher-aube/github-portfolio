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

6. Under the workflow sidebar, there should be a `Deploy Site` link, go there.

7. You should see a run being queued or in progress.

8. After the workflow completes go to the Settings page.

9. Under the sidebar there is a `Pages` section, go there.

10. In Build and deployment section, click the `None` button under the Branch title. Select the `gh-pages` branch then `Save`.

    1. Deployments are not instant, it may take a few minutes (or 10!) for your first deployment to complete. To check in on the status/progress of your deployment, go to the Code page of your repository. In the sidebar there is an Environments section, you should see `github-pages`. Clicking that link will bring you to the deployment history of your site. An in progress deployment will appear with a yellow rocket ship icon.

11. Once the deployment is complete you'll see some messaging and a new section appear on the page tell you that your site is live. Click the `Visit site` button.

12. Your site should have the same content as your local web server.

## Next Steps

Pushing changes to main will trigger deployments, so it best practice to create branches and merge pull requests. Doing so will avoid unnecessary workflow runs.

If you want your site to have multiple pages, you may run into some trouble with routing. It is recommend to use the `HashRouter` from `react-router-dom` to achieve a multi-page site. Replace `./src/app.tsx` with the code below to get started.

```typescript
import React from 'react';
import { HashRouter as Router, Routes, Route, Navigate, Link } from 'react-router-dom';

const PageOnePath = '/';
const PageOne = () => {
  return <h1 className="heading">Page One</h1>;
}

const PageTwoPath = '/page-two';
const PageTwo = () => {
  return <h1 className="heading">Page Two</h1>;
}

export const App = () => {
  return (
    <Router>
      <main>
        <nav>
          <ul>
            <li>
              <Link to={PageOnePath}>Page One</Link>
              <Link to={PageTwoPath}>Page Two</Link>
            </li>
          </ul>
        </nav>
        <Routes>
          <Route path={PageOnePath} element={<PageOne />} />
          <Route path={PageTwoPath} element={<PageTwo />} />
          <Route path="*" element={<Navigate to={PageOnePath} />} />
        </Routes>
      </main>
    </Router>
  )
};

export default {
  App,
};
```