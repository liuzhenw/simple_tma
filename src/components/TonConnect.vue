<template>
  <div>
    <div id="ton-connect"></div>
  </div>
</template>
<script setup>
import { TonConnectUI, THEME } from "@tonconnect/ui";
import { onMounted } from "vue";

onMounted(async () => {
  const connector = new TonConnectUI({
    manifestUrl: "https://192.168.31.6:8080/tonconnect-manifest.json",
    buttonRootId: "ton-connect",
  });
  connector.uiOptions = {
    language: "zh-hans",
    uiPreferences: {
      theme: THEME.DARK,
    },
    twaReturnUrl: "https://t.me/astra_tma_bot/simple_tma",
  };
  console.debug(connector);
  const wallets = await connector.getWallets();
  console.debug(wallets);

  connector.onStatusChange((status) => {
    console.debug(`Connection status: ${status}`);
  });
});
</script>
<style scoped>
#ton-connect {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
