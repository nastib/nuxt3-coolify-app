<template>
  <div>
    <NuxtRouteAnnouncer />
    <div>Hello World</div>
    <div>
      <iframe :src="iframeUrl" frameborder="0" width="1600" height="1600" allowtransparency></iframe>
    </div>
    <!-- <NuxtWelcome /> -->
  </div>
</template>

<script setup lang="ts">
// you will need to install via 'npm install jsonwebtoken' or in your package.json

import jwt from 'jsonwebtoken';

const METABASE_SITE_URL = 'https://metabasech.digitlab.app';
const METABASE_SECRET_KEY = '35b09a09f70004e206743985bd9b39aa01dd35c040b5db7067865c3b1188a314';

const payload = {
  resource: { dashboard: 3 },
  params: {},
  exp: Math.round(Date.now() / 1000) + 10 * 60, // 10 minute expiration
};
const token = jwt.sign(payload, METABASE_SECRET_KEY);

const iframeUrl = METABASE_SITE_URL + '/embed/dashboard/' + token + '#theme=night&#bordered=true&titled=true';
</script>
