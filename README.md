# ShmooCon Ticket Bot PoC 🎫🤖
*This is a proof-of-concept bot to automatically purchase tickets for ShmooCon, a conference that is notoriously hard to get tickets for. This repository serves as a directory for everything that has been orchestrated for this.*

> [!CAUTION]
> This project is provided for research and educational purposes only. It is intended solely as a proof of concept. The author is not responsible for any misuse or actions taken by end users based on this code. Use at your own risk.

## About
This project was an attempt to see what a working ticket bot would look like for ShmooCon, considering that it was the last year the conference was occurring. A lot of effort was put into this project over the years, including a feature for automatically answering the riddles using AI. Everything was written in TypeScript and I would definitely consider this overengineered (but that just makes it even more fun!).

[A talk was even done on this very thing! (~2 hour mark)](https://archive.org/details/shmoocon2025/ShmooCon2025-Firetalks_2025.mp4)

## Architecture
Everything was ran with Docker. Below is the architecture for the latest proof-of-concept:
- [dashboard](https://github.com/ShmooConTix/dashboard): Served as the "user-facing" portion of the bot and was where configuration (accounts, URLs, etc.) was managed. Build with NextJS and a very nice UI.
- [bot-ts](https://github.com/ShmooConTix/bot-ts): The actual "bot," which used Playwright to execute its commands. Used a "stages" system to execute its tasks. Handles errors incredibly and communicates with the API.
- [ticket-server](https://github.com/ShmooConTix/ticket-server): Acted as a replicated mock version of the ShmooCon ticket server, as using the real ShmooCon ticket server would be unwanted. Built with Bun, SQLite, Elysia, and React.
- [api](https://github.com/ShmooConTix/api): Did the "heavy lifting" / processing for the bot. Handled AI responses, configuration, and user management. Communicated with `bot-ts`, `extension`, and `dashboard`. Built with Bun, SQLite, and Elysia.
- [extension](https://github.com/ShmooConTix/extension): Sent the riddle to the API, retrieved the answer, and input it. Meant for a human version (which was not the final version, still a cool concept though). **THIS WAS MORE OF A CONCEPT AND IS NOT PART OF THE FINAL VERSION.**

Below is a diagram of the above (for the final version):
![image](https://github.com/user-attachments/assets/e358d056-1ad2-42a0-bf50-b6abb33c5f26)

## Contributing
This project / experiment is over and is not open to changes. Please contact me if you have questions.
