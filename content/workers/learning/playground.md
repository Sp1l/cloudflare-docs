---
pcx_content_type: concept
title: Playground
---

# Playground

The quickest way to experiment with Cloudflare Workers is in the [Playground](https://workers.cloudflare.com/playground). It does not require any setup or authentication. The Playground is a sandbox which gives you an instant way to preview and test a Worker script directly in the browser.

It uses the same editor and preview service as the authenticated experience, and provides the ability to share the code you write as well as deploy it instantly to Cloudflare's global network. This way, you can quickly try new things out and deploy them when you're ready.

<p>{{<button type="primary" href="https://workers.cloudflare.com/playground">}}Launch playground{{</button>}}</p>

---

## Hello Cloudflare Workers

When you arrive in the playground, you will see this default code:

```js
import welcome from "welcome.html";

/**
 * @typedef {Object} Env
 */

export default {
  /**
   * @param {Request} request
   * @param {Env} env
   * @param {ExecutionContext} ctx
   * @returns {Response}
   */
  fetch(request, env, ctx) {
    console.log("Hello Cloudflare Workers!");

    return new Response(welcome, {
      headers: {
        "content-type": "text/html",
      },
    });
  },
};
```

This is an example of a multi-module Worker that is receiving a [request](/workers/runtime-apis/request/), logging a message to the console, and then returning a [response](/workers/runtime-apis/response/) body that is content from `welcome.html`.

Refer to the documentation for [`Fetch Handler`](/workers/runtime-apis/handlers/fetch/) to learn more.

---

## Using the Playground

As you edit the default code, the Worker will auto-update allowing you to see a preview on the right side running just as it would in a browser. If your Worker uses URL paths, you can enter those in the input field on the right to navigate. The editor provides type-checking via JSDoc comments and `workers-types` and also provides pretty error pages in the event of app errors.

To test a raw HTTP request — not in the HTML previewer, for example, to test a `POST` request — go to the **HTTP** tab and click **Send**. You can add and edit headers via this panel, as well as edit the body of a request.

---

## DevTools

For debugging Workers inside the Playground, use the developer tools at the bottom of the Playground's preview panel to view `console.logs`, see network requests, and view memory and cpu usage. The developer tools for the Workers Playground work similar to the developer tools in Chrome or Firefox, and are the same developer tools users have access to in the [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/) and the authenticated dashboard.

### Network tab

**Network** shows the outgoing requests from your Workers script — that is, any calls to `fetch` inside your script.

### Console Logs

The console displays the output of any calls to `console.log` that were called for the current preview run as well as any other preview runs in that session.

### Sources

**Sources** displays the sources that make up your Workers script. Note that access KV, text, and secret bindings are only accessible when authenticated with an account. This means you must be logged in to the dashboard, or use `wrangler dev` with your account credentials.

## Share

To share what you've created, click on the **Copy Link** button in the top right of the screen. This will copy a unique URL to your clipboard that you can share with anyone. These links do not expire, so you can bookmark your creation and share it at any time. Users that open a shared link will see the Playground with the shared code and preview.

## Deploy

You can deploy a Worker straight from the Playground. If you're already logged in, you'll be able to review the Worker before deploying. Otherwise, you'll be taken through the first-time user onboarding flow before you can review and deploy.

Once deployed, your Worker will get its own unique URL and be available almost instantly on Cloudflare's global network. From here, you can add custom domains, storage resources, and more.
