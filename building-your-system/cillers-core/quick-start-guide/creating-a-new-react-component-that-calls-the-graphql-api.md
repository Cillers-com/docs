# Creating A New React Component That Calls The GraphQL API

The frontend web app code is located in the `code/web-app/src` directory. When authenticate the `Authenticated` component in the `code/web-app/src/components` acts as the main container.&#x20;

Let's replace the `Products` sample component with a new component, called `Hello`, and make it call the hello GraphQL operation and render the response. &#x20;

<pre class="language-tsx"><code class="lang-tsx">import React from 'react'; 
import { ApolloProvider } from '@apollo/client';
import create_api_client from '../utils/apolloClient';
<a data-footnote-ref href="#user-content-fn-1">import Hello from './Hello';</a>

interface AuthenticatedProps {
  userInfo: Record&#x3C;string, any>; 
  logout: () => void; 
  csrf: string;
}

function on_graphql_error(messages: string[]) { 
    messages.forEach(message => alert(message)); 
} 

const Authenticated: React.FC&#x3C;AuthenticatedProps> = ({ userInfo, logout, csrf }) => {
    return (
        &#x3C;ApolloProvider client={create_api_client(csrf, on_graphql_error)}>
            &#x3C;div>
                Authenticated as: {JSON.stringify(userInfo)}
            &#x3C;/div>
            &#x3C;button onClick={logout}>
                Logout
            &#x3C;/button>
            <a data-footnote-ref href="#user-content-fn-2">&#x3C;Hello /></a>
        &#x3C;/ApolloProvider>
    )
} 

export default Authenticated;


</code></pre>

Create a new file `Hello.tsx` in the components directory.&#x20;

```tsx
import { useQuery } from '@apollo/client';
import { GET_HELLO } from '../graphql/operations';

interface HelloQuery {
  message: string;
}

const Hello: React.FC = () => {
  const { data, loading, error } = useQuery(GET_HELLO);

  if (loading) return (
    <div className="flex justify-center items-center min-h-screen bg-base-300">
      <button className="btn">
        <span className="loading loading-spinner"></span>
        Loading...
      </button>
    </div>
  );
  if (error) return <p>{'Error: ' + error}</p>;

  return (
    <div className="min-h-screen flex flex-col">
      <div className="navbar bg-base-300 text-neutral-content">
        <div className="flex-1">
          {"Message: " + data.hello.message}
        </div>
      </div>
    </div>
  );
};

export default Hello;
```

[^1]: Import Hello instead of Products

[^2]: Change from Products to Hello
