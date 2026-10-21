# friendlyBrandon Portfolio

A responsive portfolio website for **friendlyBrandon**, a graduate programming student with experience in C#, Java, and JavaScript. The site presents selected project work, community involvement, ProxyBase as a business, and links to GitHub, LinkedIn, ProxyBase, and Mysterium Network. It is built with Vue 3 and Vite and remains a static site without accounts, a message inbox, or a backend.

## Development

Install dependencies with `npm install`, then use:

- `npm run dev` — start the Vite development server.
- `npm run build` — create the production site in `dist/`.
- `npm run preview` — preview the production build locally.

Open the local URL printed by Vite after starting `npm run dev` or `npm run preview`.
If the default port (5173) is already in use, Vite automatically chooses another
port, such as 5174. Opening `index.html` directly from the file system does not
start the app; it needs to be served by Vite or another static web server.

## GitHub Pages deployment

GitHub Pages must publish the Vite production output, not the repository's source
`index.html`. The workflow in `.github/workflows/deploy.yml` builds the app and
publishes `dist/` when changes are pushed to `main`. In the repository settings,
open **Pages** and set **Build and deployment → Source** to **GitHub Actions**.

This repository is named `new-gh`, so its GitHub Pages project URL is
`https://friendlybrandon.github.io/new-gh/`. The root URL
`https://friendlybrandon.github.io/` is reserved for a user site and requires a
repository named `friendlyBrandon.github.io` (GitHub URLs are case-insensitive).
Rename this repository to that exact name if the root URL is the intended one.

## Project files

- `index.html` — Vite entry page and document metadata.
- `src/main.js` — Vue application entry point and stylesheet import.
- `src/App.vue` — portfolio content, responsive navigation, and theme interaction.
- `styles.css` — responsive layout, illustrations, and dark/light theme colors.
- `vite.config.js` — Vite configuration.
- `package.json` — Vue/Vite dependencies and project scripts.
- `duckinglogo.png` — the supplied ProxyBase logo.
- `public/myst.png` — the supplied Mysterium Network logo, served as a static asset.

## What the portfolio includes

- An introduction identifying the portfolio owner as `friendlyBrandon` and a graduate programming student.
- C#, Java, and JavaScript as programming languages in the toolkit.
- An AquaFin project card linking to [friendlyBrandon/AquaFin_Project](https://github.com/friendlyBrandon/AquaFin_Project). Its description covers the Laravel application, Python rainfall-forecasting service, flood-preparedness recommendations, dashboard, charts, and materials cart.
- A Mysterium Network community-helper section using `myst.png` as the network logo.
- A ProxyBase business section using `duckinglogo.png`, with public-site details about residential proxies, usage-based pricing advertised from $0.75/GB, and card or cryptocurrency top-ups starting at $1.
- Links to the GitHub profile, LinkedIn profile, ProxyBase, and Mysterium Network.
- Responsive desktop and mobile navigation, custom project illustrations, and a dark/light appearance toggle.

Dark mode is the default. The theme control updates the page colors and browser theme-color metadata. The mobile menu is collapsible and closes when a navigation link is selected.

## Decisions and requested changes

The portfolio was created from an initially empty workspace rather than adapted from an existing site. Its visual direction is a restrained, professional layout with a dark default palette, muted green accents, typography, and CSS-drawn project previews.

The requested changes incorporated during development were:

1. Create a portfolio using the supplied graduate-programming and language details.
2. Link and explain the AquaFin GitHub project, include ProxyBase and Mysterium Network, and use the supplied ProxyBase logo.
3. Refine the presentation, make dark mode the default, and add a light-mode toggle.
4. Remove the archived Mysterium staking bot from the portfolio.
5. Use `friendlyBrandon` instead of the owner's real name in portfolio content.
6. Expand the ProxyBase description using information from its public site and identify ProxyBase as the owner's business.
7. Remove the claim that ProxyBase balances do not expire and improve the contrast of the contact section in light mode.
8. Document the work and possible improvements in this README.
9. Follow `AGENTS.md` by migrating the site to Vue 3 and Vite, keeping it static, keyboard-usable, and responsive, and making ProxyBase's business status explicit.

The LinkedIn profile could not be accessed automatically while creating the portfolio, so LinkedIn-specific education and employment history were not added or inferred. Project and ProxyBase descriptions use publicly accessible GitHub and service-page information alongside the details supplied in the request.

## Validation performed

- Ran `npm run build`; Vite created the production bundle in `dist/`.
- Started the Vite development server and confirmed the page, Vue entry module, and Mysterium logo returned HTTP 200. When port 5173 was occupied, Vite selected port 5174; opening the printed URL served the portfolio correctly.
- The previous visual checks covered the mobile menu, theme switching, ProxyBase logo loading, horizontal overflow at mobile/tablet/desktop widths, and light-mode contact text contrast.

There is no automated test suite; the production build is the project-level validation command.

## Startup troubleshooting

If the expected page does not appear at `http://localhost:5173`, check the URL
printed in the terminal after `npm run dev`. A port conflict makes Vite serve the
site on the next available port. For GitHub Pages, check the Actions tab for a
successful deployment and confirm Pages uses **GitHub Actions** as its source;
publishing the repository root serves unbuilt Vue source and leaves the page blank.

## What could be improved

- Add a real email/contact method or a contact form; the current contact area links to LinkedIn and GitHub.
- Add confirmed education details, relevant coursework, and work history once the owner provides or verifies them.
- Add screenshots or a live demo for AquaFin if available, and clarify the owner's specific contribution to the project.
- Add more non-archived projects after reviewing their public repositories and deciding which best represent the owner's work.
- Consider saving the chosen theme between visits, for example with `localStorage`.
- Run an accessibility review with a dedicated checker and test with keyboard navigation and screen readers.
- Add automated browser tests if the site grows beyond a small static page.
