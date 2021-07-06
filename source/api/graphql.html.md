---
title: "GraphQL"
---

If you are interested in exploring our GraphQL, you can do that using the following endpoint in an application like [graphiql]( https://www.electronjs.org/apps/graphiql) or using the GraphQL explorer below.

## Base URL
```
https://appsignal.com/graphql?token=[token]
```
You can get the token from https://appsignal.com/users/edit

## Explorer
<div id="graphiql" style="height: 100vh;">Loading..</div>

<!-- GraphiQL -->

<script crossorigin src="https://unpkg.com/react/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom/umd/react-dom.production.min.js"></script>
<script crossorigin src="https://unpkg.com/graphiql/graphiql.min.js"></script>
<link href="https://unpkg.com/graphiql/graphiql.min.css" rel="stylesheet" />


<script>
  function graphQLFetcher(graphQLParams) {
    return fetch(
      'https://appsignal.com/graphql?token=',
      {
        method: 'post',
        headers: {
          Accept: 'application/json',
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(graphQLParams),
        credentials: 'omit',
      },
    ).then(function (response) {
      return response.json().catch(function () {
        return response.text();
      });
    });
  }

  ReactDOM.render(
    React.createElement(GraphiQL, {
      fetcher: graphQLFetcher,
      defaultVariableEditorOpen: true,
    }),
    document.getElementById('graphiql'),
  );
</script>
