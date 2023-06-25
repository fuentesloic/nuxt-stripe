# Nuxt module for Stripe

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![License][license-src]][license-href]
[![Nuxt][nuxt-src]][nuxt-href]

Nuxt module for application using stripe.

- [✨ &nbsp;Release Notes](/CHANGELOG.md)
- [🏀 Online playground](https://stackblitz.com/github/fuentesloic/nuxt3-stripe?file=playground%2Fapp.vue)
<!-- - [📖 &nbsp;Documentation](https://example.com) -->

## Features

This Nuxt module provides an easy way to integrate Stripe in your Nuxt application, both on the client-side and server-side. It utilizes the official `stripe` package for server-side usage and @stripe/stripe-js for the client-side.

### Server-side usage

The module provides a `useServerStripe` function to create a Stripe instance on the server-side.
This instance can be used to interact with the Stripe API.

#### Example
```ts
import { defineEventHandler } from 'h3';
import { useServerStripe } from '#stripe/server'

export default defineEventHandler(async (event) => {
  const stripe = await useServerStripe(event)
  console.info("Stripe instance:", stripe)

  return {
    version: stripe.VERSION
  }
});

```

### Client-side usage

On the client-side, you can use the `useClientStripe` function to get a Stripe instance.
This instance can be used in pages or plugins.

Use stripe inside pages or plugins

#### Example
```vue
<template>
  <h1>Nuxt Stripe instance</h1>
  <div>
    {{ stripe }}
  </div>
</template>

<script setup lang="ts">
import { useClientStripe } from '#imports';

const stripe = useClientStripe()
</script>
```

## Quick Setup

1. Add `@nuxtjs/stripe` dependency to your project

```bash
# Using pnpm
pnpm add -D @nuxtjs/stripe

# Using yarn
yarn add --dev @nuxtjs/stripe

# Using npm
npm install --save-dev @nuxtjs/stripe
```

2. Add `@nuxtjs/stripe` to the `modules` section of `nuxt.config.ts`

```ts
export default defineNuxtConfig({
  modules: [
    '@nuxtjs/stripe'
  ],
  stripe: {
    apiKey: 'sk_test_123',
    publishableKey: 'pk_test_123',
  }
})
```

## Configuration

You can configure the module by providing the necessary Stripe keys and an optional API version in your `nuxt.config.js` file:

```ts
export default defineNuxtConfig({
  modules: [
    '@nuxtjs/stripe'
  ],
  stripe: {
    // Server
    apiKey: 'sk_test_123', // required
    apiVersion: '2022-11-15', // optional, default is '2022-11-15'
    // client
    publishableKey: 'pk_test_123', // required
  }
})
```

## Development

```bash
# Install dependencies
npm install

# Generate type stubs
npm run dev:prepare

# Develop with the playground
npm run dev

# Build the playground
npm run dev:build

# Run ESLint
npm run lint

# Run Vitest
npm run test
npm run test:watch

# Release new version
npm run release
```

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/@nuxtjs/stripe/latest.svg?style=flat&colorA=18181B&colorB=28CF8D
[npm-version-href]: https://npmjs.com/package/@nuxtjs/stripe

[npm-downloads-src]: https://img.shields.io/npm/dm/@nuxtjs/stripe.svg?style=flat&colorA=18181B&colorB=28CF8D
[npm-downloads-href]: https://npmjs.com/package/@nuxtjs/stripe

[license-src]: https://img.shields.io/npm/l/@nuxtjs/stripe.svg?style=flat&colorA=18181B&colorB=28CF8D
[license-href]: https://npmjs.com/package/@nuxtjs/stripe

[nuxt-src]: https://img.shields.io/badge/Nuxt-18181B?logo=nuxt.js
[nuxt-href]: https://nuxt.com
