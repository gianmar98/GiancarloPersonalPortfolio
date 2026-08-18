# Giancarlo Martinez - Personal Portfolio

A modern, responsive single-page portfolio website showcasing expertise in AWS cloud computing, data analytics, and machine learning engineering.

**Live Site**: [giancarlomartinez.com](https://giancarlomartinez.com)

---

## Overview

Personal portfolio built as a static site with no frameworks or build tools — plain HTML5, CSS3, and minimal vanilla JavaScript. Deployed on AWS with CloudFront, S3, Route 53, and ACM.

---

## Tech Stack

### Frontend
- **HTML5** — semantic markup with Schema.org JSON-LD structured data for SEO
- **CSS3** — Flexbox, Grid, backdrop-filter blur, CSS animations
- **Vanilla JavaScript** — lightweight inline DOM manipulation
- **Devicon CDN** — technology icons

### Cloud Infrastructure
- **AWS S3** — static website hosting
- **AWS CloudFront** — global CDN with HTTPS enforcement
- **AWS Route 53** — DNS and custom domain routing
- **AWS Certificate Manager** — SSL/TLS certificate provisioning

---

## Architecture

![AWS architecture for giancarlomartinez.com: Route 53 aliases route apex and www traffic to two CloudFront distributions over S3 website origins](portfolioArchitecture.png)

Both hostnames are served end to end by AWS managed services — there is no server to patch.

| Step | What happens |
|---|---|
| 1 | The browser resolves `giancarlomartinez.com` or `www.giancarlomartinez.com` against the Route 53 public hosted zone. |
| 2-3 | `A` alias records point each hostname at its own CloudFront distribution. |
| 4-5 | A single ACM certificate in `us-east-1` covers both hostnames as SANs and is attached to both distributions. Viewer policy is `redirect-to-https` with `sni-only`. DNS validation via CNAME records in the same zone keeps renewal automatic. |
| 6 | The apex distribution fetches from the S3 **website endpoint** as a custom origin. Because it is a website endpoint rather than a REST endpoint, OAC/OAI does not apply and the bucket policy grants public `s3:GetObject`. |
| 7-8 | The `www` bucket holds no objects; it is configured `RedirectAllRequestsTo` the apex hostname and answers `301`, sending the browser back to step 1. |

Editable source: [`portfolioArchitecture.drawio`](portfolioArchitecture.drawio) — open at [app.diagrams.net](https://app.diagrams.net).

---

## Project Structure

All files live flat in the root — no asset subdirectories.

```
GiancarloPersonalPortfolio/
├── index.html               # Entire site (all sections)
├── style.css                # All styles
├── README.md                # This file
├── Giancarlo_Martinez.pdf   # Resume
├── git.ignore               # Local ignore list
├── portfolioArchitecture.png    # AWS architecture diagram
├── portfolioArchitecture.drawio # Diagram source (draw.io)
├── enactus.jpeg
├── gianAYSO.jpeg
├── gianGuate23s.jpeg
├── gianUAH.jpeg
├── hcfcGian.JPG
├── microsoft-power-apps.png
└── reInventGian.jpg
```

---

## Page Sections

1. **Header** — Name, scripture quote, social links, resume download
2. **Navigation** — Sticky nav bar with smooth anchor scrolling
3. **Summary** — Professional bio and certifications overview
4. **Skills** — Icon grid organized by Cloud, Programming, Data Analysis, and Other
5. **Work Experience** — MTM (current), Designalytics, UAH, HCFC
6. **Projects** — AWS capstone, portfolio site deployment, AI pathfinding, and more
7. **Extracurriculars** — Professional soccer, Enactus, AWS re:Invent
8. **Education** — UAH degrees + Amazon Cloud Institute
9. **Certifications** — Interactive badge cards linked to Credly

---

## Certifications

| Certification | Status |
|---|---|
| AWS ML Engineer Associate (MLA) | In Progress |
| Terraform Associate (004) | Earned |
| AWS ML Specialty (MLS-C01) | Earned |
| AWS Data Engineer Associate (DEA-C01) | Earned |
| AWS Solutions Architect Associate (SAA-C03) | Earned |
| AWS AI Practitioner | Earned |
| AWS Cloud Practitioner | Earned |

---

## Current Role

**Mazda Toyota Manufacturing (MTM)** — Specialist, Data Analytics & Systems Development *(July 2025 – Present)*

Key deliverables:
- **Abnormal Tracker** — Plant-wide Power Apps parts accountability app; migrated 49,000 historical records, saves ~63 hrs/year of manual input. Est. value $50K–$100K.
- **AWS R&D (Plant Innovation Lead)** — Leading plant-wide AWS initiative; architecting proof-of-concept for AWS IoT SiteWise.
- **ICS API** — 3 Python REST APIs + 2 Power BI dashboards (~3,000 lines); eliminates 137.5 hrs/year of manual work. Est. value $50K.
- **Assembly Kaizen** — First Power Apps build from scratch; delivered 2 weeks ahead of a 4-week plan. Est. value $50K.
- **QLC App** — Quality Dojo scheduling app for full Team Leader population; delivered 1 week ahead of a 1-month scope. Est. value $50K.

---

## Local Development

No setup required — open `index.html` directly in any modern browser.

```bash
git clone https://github.com/gianmar98/GiancarloPersonalPortfolio.git
cd GiancarloPersonalPortfolio
open index.html
```

---

## Contact

- **Email**: [giancusm@gmail.com](mailto:giancusm@gmail.com)
- **LinkedIn**: [linkedin.com/in/gmo1998](https://www.linkedin.com/in/gmo1998)
- **GitHub**: [github.com/gianmar98](https://github.com/gianmar98)

---

© 2025 Giancarlo Martinez. All rights reserved.