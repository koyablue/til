# Configure Hot Reload

In vite.config.ts

```
export default defineConfig({
  plugins: [vue()],
  server: {
    watch: {
      usePolling: true
    }
  }
})

```
