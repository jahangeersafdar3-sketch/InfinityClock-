# Security Notes

- Do not commit API keys, signing keystores, passwords, or service-account files.
- Remote AI providers, if enabled later, must be accessed through a protected server/proxy or another mechanism that does not embed private credentials in the APK.
- The local AI path produces validated structured clock data; it does not execute generated Kotlin, Java, JavaScript, or shell commands.
- For release signing, store credentials in GitHub Actions secrets or another secure CI secret store.
