

  # Using Speakeasy with React

## Introduction

Speakeasy provides powerful tools for generating SDKs and code samples. This guide will walk you through how to use Speakeasy-generated code in your React applications.

## Installation

First, install the Speakeasy-generated SDK for your API:

```bash
npm install @speakeasyapi/code-samples
```

## Setting Up

To use the Speakeasy SDK in your React application, you need to set up the necessary providers:

1. Import the required components:

```jsx
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { SpeakeasyCodeSamplesCore } from "@speakeasyapi/code-samples";
import { SpeakeasyCodeSamplesProvider } from "@speakeasyapi/code-samples/react-query";
```

2. Create instances of QueryClient and SpeakeasyCodeSamplesCore:

```jsx
const queryClient = new QueryClient();
const speakeasyCodeSamples = new SpeakeasyCodeSamplesCore({
  apiKey: "<YOUR_API_KEY_HERE>",
  registryUrl: "https://spec.speakeasy.com/org/ws/my-source",
});
```

3. Wrap your app with the necessary providers:

```jsx
export function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <SpeakeasyCodeSamplesProvider client={speakeasyCodeSamples}>
        {/* Your app components */}
      </SpeakeasyCodeSamplesProvider>
    </QueryClientProvider>
  );
}
```

## Making API Calls

Speakeasy generates React hooks for each API endpoint. Here's how to use them:

```jsx
import { useCodeSamples } from "@speakeasyapi/code-samples/react-query/codeSamplesGet.js";

export function Example() {
  const { data, error, status } = useCodeSamples({
    registryUrl: "https://spec.speakeasy.com/my-org/my-workspace/my-source",
    operationIds: ["getPets"],
    methodPaths: [{ method: "get", path: "/pets" }],
    languages: ["python", "javascript"],
  });

  if (status === "loading") return <div>Loading...</div>
;
  if (status === "error") return <div>Error: {error.message}</div>
;

  return (
    <div>
      {/* Render your data here */}
    </div>

  );
}
```

## Advanced Usage

### Query Options

You can pass additional options to control caching, retries, and timeouts:

```jsx
const { data, error, status } = useCodeSamples(
  {
    // ... request parameters
  },
  {
    staleTime: 60 * 1000, // 1 minute
    gcTime: 5 * 60 * 1000, // 5 minutes
    timeoutMs: 1000,
    retryCodes: ["5XX"],
    retries: {
      strategy: "backoff",
      backoff: {
        initialInterval: 500,
        maxInterval: 10 * 1000,
        exponent: 1.5,
        maxElapsedTime: 60 * 1000,
      },
    },
  }
);
```

### Cache Invalidation

To invalidate cache after mutations:

```jsx
import { useQueryClient } from "@tanstack/react-query";
import { invalidateCodeSamples, invalidateAllCodeSamples } from "@speakeasyapi/code-samples/react-query/codeSamplesGet.js";

export function Example() {
  const queryClient = useQueryClient();

  const handleSubmit = () => {
    // Perform mutation
    // Then invalidate cache:
    invalidateCodeSamples(queryClient, /* ... arguments ... */);
    // Or invalidate all cache entries:
    invalidateAllCodeSamples(queryClient);
  };

  // ... rest of the component
}
```

### React Suspense Integration

Speakeasy also provides hooks that integrate with React Suspense:

```jsx
import { useCodeSamplesSuspense } from "@speakeasyapi/code-samples/react-query/codeSamplesGet.js";

function Example() {
  const { data } = useCodeSamplesSuspense({
    // ... request parameters
  });

  return (
    <div>
      {/* Render your data here */}
    </div>

  );
}

// Wrap with Suspense in parent component:
<React.Suspense fallback={<div>Loading...</div>
}>
  <Example />
</React.Suspense>
```

### Server-Side Rendering

For SSR or React Server Components, use the `prefetch` functions:

```jsx
import { dehydrate, HydrationBoundary, QueryClient } from "@tanstack/react-query";
import { SpeakeasyCodeSamplesCore } from "@speakeasyapi/code-samples";
import { prefetchCodeSamples } from "@speakeasyapi/code-samples/react-query/codeSamplesGet.js";

export default async function Page() {
  const queryClient = new QueryClient();
  const speakeasyCodeSamples = new SpeakeasyCodeSamplesCore({
    apiKey: "<YOUR_API_KEY_HERE>",
    registryUrl: "https://spec.speakeasy.com/org/ws/my-source",
  });

  await prefetchCodeSamples(queryClient, speakeasyCodeSamples, {
    // ... request parameters
  });

  return (
    <HydrationBoundary state={dehydrate(queryClient)}>
      {/* Your components */}
    </HydrationBoundary>
  );
}
```

## Conclusion

By following this guide, you should now be able to effectively use Speakeasy-generated SDKs in your React applications, leveraging the power of React Query for efficient data fetching and caching.

  