Do we store any data?
- we do not have a server. Our 3rd party data services include GitHub, Clerk, OpenAI, and Claude.
Where are my past conversations?
- because we do not store any of your data, we are limited to the endpoints provided by our service providers. OpenAI does not provide the ability to fetch conversations.
Can we use Codex instead of Claude Code?
- it’s in development! 
My GitHub issues are not running Claude
- ensure you have the appropriate GitHub workflow file installed by running /install-github-app in your local repository
Is my token secure?
- absolutely. It’s stored client-side within your browser. We never see it and we never want to!
My api key is not syncing between devices
- your key is stored on the browser you inputted it to. This means you must input it every time you start a session on a new device or clear your local storage.
Why is it speaking to me in a different language?
- I cannot set a language for the voice agent so it will respond in whichever language it believes you are attempting to speak in.