# friendlyBrandon Portfolio

A responsive, static portfolio website for **friendlyBrandon**, a graduate programming student with experience in C#, Java, and JavaScript. The site presents selected project work, community involvement, and links to GitHub, LinkedIn, ProxyBase, and Mysterium Network.

## View the site

Open `index.html` in a browser. No build step or package installation is needed. For local development, you can also serve the folder with any static web server.

## Project files

- `index.html` — semantic page structure, portfolio content, and external links.
- `styles.css` — responsive layout, illustrations, and dark/light theme colors.
- `script.js` — mobile navigation, theme toggle, and current-year footer.
- `duckinglogo.png` — the supplied ProxyBase logo.

## What the portfolio includes

- An introduction identifying the portfolio owner as `friendlyBrandon` and a graduate programming student.
- C#, Java, and JavaScript as programming languages in the toolkit.
- An AquaFin project card linking to [friendlyBrandon/AquaFin_Project](https://github.com/friendlyBrandon/AquaFin_Project). Its description covers the Laravel application, Python rainfall-forecasting service, flood-preparedness recommendations, dashboard, charts, and materials cart.
- A Mysterium Network community-helper section.
- A ProxyBase section using `duckinglogo.png`, with public-site details about residential proxies, usage-based pricing advertised from $0.75/GB, and card or cryptocurrency top-ups starting at $1.
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
6. Expand the ProxyBase description using information from its public site.
7. Remove the claim that ProxyBase balances do not expire and improve the contrast of the contact section in light mode.
8. Document the work and possible improvements in this README.

The LinkedIn profile could not be accessed automatically while creating the portfolio, so LinkedIn-specific education and employment history were not added or inferred. Project and ProxyBase descriptions use publicly accessible GitHub and service-page information alongside the details supplied in the request.

## Validation performed

- Checked JavaScript syntax and parsed the HTML.
- Opened the page in a browser and checked the mobile menu, theme switching, and ProxyBase logo loading.
- Checked for horizontal overflow at mobile, tablet, and desktop viewport widths.
- Checked the light-mode contact-section text contrast in the browser.

There is no automated test suite or build configuration in this static project.

## What could be improved

- Add a real email/contact method or a contact form; the current contact area links to LinkedIn and GitHub.
- Add confirmed education details, relevant coursework, and work history once the owner provides or verifies them.
- Add screenshots or a live demo for AquaFin if available, and clarify the owner's specific contribution to the project.
- Add more non-archived projects after reviewing their public repositories and deciding which best represent the owner's work.
- Consider saving the chosen theme between visits, for example with `localStorage`.
- Run an accessibility review with a dedicated checker and test with keyboard navigation and screen readers.
- Add automated browser tests if the site grows beyond a small static page.
