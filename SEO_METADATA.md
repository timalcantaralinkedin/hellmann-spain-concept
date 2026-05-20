# SEO Metadata — Hellmann Spain Landing Page

Reference document for the Hellmann Spain country landing page concept. All values are implemented in `index.html` and ready for transfer to the Drupal CMS metadata fields.

---

## 1. Title tag

**Length:** 71 characters

```
Transport and Logistics | Hellmann Spain | Hellmann Worldwide Logistics
```

Format matches the live Hellmann Saudi Arabia page (`Transport and Logistics | Hellmann Saudi Arabia | Hellmann Worldwide Logistics`).

---

## 2. Meta description

**Length:** 157 characters

```
Hellmann Worldwide Logistics Spain provides airfreight, seafreight, road, rail and contract logistics from offices in Barcelona, Madrid, Bilbao and Valencia.
```

---

## 3. Meta keywords

```
Hellmann Spain, freight forwarding Spain, logistics Spain, airfreight Spain, seafreight Spain, contract logistics Spain, Barcelona logistics, Madrid logistics, Bilbao logistics, Valencia logistics
```

---

## 4. Canonical and indexing

| Field | Value |
|---|---|
| Eventual canonical (production target) | `https://www.hellmann.com/en/europe/transport-and-logistics-hellmann-spain` |
| Current canonical (preview) | `https://hellmann-spain-concept.netlify.app/` |
| Robots | `noindex, nofollow` (private concept preview; switch to `index, follow` after Drupal publication) |
| Author | Hellmann Worldwide Logistics |

---

## 5. Open Graph (Facebook, LinkedIn, Slack previews)

```
og:type        website
og:url         https://hellmann-spain-concept.netlify.app/
og:title       Transport and Logistics | Hellmann Spain | Hellmann Worldwide Logistics
og:description Hellmann Worldwide Logistics Spain provides airfreight, seafreight, road, rail and contract logistics from offices in Barcelona, Madrid, Bilbao and Valencia.
og:image       https://images.unsplash.com/photo-1605281317010-fe5ffe798166?w=1200&q=80
og:site_name   Hellmann Worldwide Logistics
og:locale      en_GB
```

---

## 6. Twitter Card

```
twitter:card        summary_large_image
twitter:title       Transport and Logistics | Hellmann Spain | Hellmann Worldwide Logistics
twitter:description Airfreight, seafreight, road, rail and contract logistics from offices in Barcelona, Madrid, Bilbao and Valencia.
twitter:image       https://images.unsplash.com/photo-1605281317010-fe5ffe798166?w=1200&q=80
```

---

## 7. JSON-LD structured data

Two linked schema entities: `Organization` (parent Hellmann Worldwide Logistics) and `LocalBusiness` (Hellmann Spain subsidiary).

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.hellmann.com/#organization",
      "name": "Hellmann Worldwide Logistics",
      "url": "https://www.hellmann.com",
      "logo": "https://www.hellmann.com/themes/hwl/assets/images/logo.svg",
      "foundingDate": "1871",
      "sameAs": [
        "https://www.linkedin.com/company/hellmann-worldwide-logistics",
        "https://en.wikipedia.org/wiki/Hellmann_Worldwide_Logistics"
      ]
    },
    {
      "@type": "LocalBusiness",
      "@id": "https://hellmann-spain-concept.netlify.app/#localbusiness",
      "name": "Hellmann Worldwide Logistics Spain",
      "parentOrganization": { "@id": "https://www.hellmann.com/#organization" },
      "description": "International freight forwarding and contract logistics services across Spain. Founded in 1999, Hellmann Spain operates from four locations with 160 local specialists.",
      "url": "https://www.hellmann.com/en/europe/transport-and-logistics-hellmann-spain",
      "areaServed": { "@type": "Country", "name": "Spain" },
      "foundingDate": "1999",
      "numberOfEmployees": "160",
      "location": [
        { "@type": "Place", "name": "Barcelona",
          "address": { "@type": "PostalAddress", "addressLocality": "El Prat de Llobregat", "addressRegion": "Barcelona", "addressCountry": "ES" } },
        { "@type": "Place", "name": "Madrid",
          "address": { "@type": "PostalAddress", "addressLocality": "San Fernando de Henares", "addressRegion": "Madrid", "addressCountry": "ES" } },
        { "@type": "Place", "name": "Bilbao",
          "address": { "@type": "PostalAddress", "addressLocality": "Bilbao", "addressRegion": "Biscay", "addressCountry": "ES" } },
        { "@type": "Place", "name": "Valencia",
          "address": { "@type": "PostalAddress", "addressLocality": "Valencia", "addressRegion": "Valencia", "addressCountry": "ES" } }
      ],
      "hasOfferCatalog": {
        "@type": "OfferCatalog",
        "name": "Logistics Services",
        "itemListElement": [
          { "@type": "OfferCatalog", "name": "Airfreight" },
          { "@type": "OfferCatalog", "name": "Seafreight" },
          { "@type": "OfferCatalog", "name": "Road and Rail Freight" },
          { "@type": "OfferCatalog", "name": "Contract Logistics" }
        ]
      }
    }
  ]
}
```

---

## 8. Heading hierarchy

One H1 per page, semantic H2 per major section, H3 for cards. No competing headings outside this structure.

| Level | Text | Location |
|---|---|---|
| H1 | Hellmann Spain | Hero |
| H2 | Welcome to Hellmann Spain | Intro |
| H2 | A country team built for industry | Facts band |
| H2 | Four locations, four areas of specialisation | Offices |
| H2 | End-to-end logistics across every mode of transport | Products |
| H2 | Industries we serve in Spain | Industries |
| H2 | The Iberia and Latin America corridor | Spotlight |
| H2 | Do business with Hellmann Spain | Contact band |
| H3 | Airfreight | Product card |
| H3 | Seafreight | Product card |
| H3 | Road and Rail | Product card |
| H3 | Contract Logistics | Product card |
| H3 | Automotive and Agricultural | Industry card |
| H3 | Fashion | Industry card |
| H3 | Consumer Goods | Industry card |
| H3 | Renewable Energy | Industry card |
| H3 | Caring, Entrepreneurial, Appreciative, Empowering, Respectful, Sustainable, Passionate | Values cards (01 to 07) |

---

## 9. Internal linking strategy

All inline and card links point to verified live Hellmann pages (every URL HEAD-checked, 21 of 21 return 200 or 302).

| Anchor | Destination |
|---|---|
| Hellmann Worldwide Logistics | /en/about-us/company |
| family-owned group | /en/about-us/company |
| seafreight | /en/products/seafreight |
| airfreight | /en/products/airfreight |
| Airfreight (product card) | /en/products/airfreight |
| Seafreight (product card) | /en/products/seafreight |
| Road and Rail (product card) | /en/products/roadfreight |
| Contract Logistics (product card) | /en/products/contract-logistics |
| Automotive and Agricultural (industry) | /en/industry-solutions/automotive-logistics |
| Fashion (industry) | /en/industry-solutions/fashion-logistics |
| Consumer Goods (industry) | /en/industry-solutions/consumer-goods |
| Renewable Energy (industry) | /en/industry-solutions/renewable-energy-logistics |
| Hellmann offices (LATAM) | /en/contact |
| Header: Products | /en/products/airfreight |
| Header: Industry Solutions | /en/industry-solutions/automotive-logistics |
| Header: About Us | /en/about-us/company |
| Header: News | /en/news-press |
| Header: Career | /en/career |
| Header: Contact | /en/contact |
| Footer: Spain transport | /en/products/spain-transport |
| Footer: Portal Login | https://portal.emea.hellmann.net/authentication/login/ |
| Footer: Legal | /en/legal |
| Footer: Privacy | /en/privacy |
| Footer: Whistleblowing | /en/whistleblowing |
| Footer: Downloads | /en/about-us/downloads |
| Footer: Contact | /en/contact |

Social links use the official Hellmann social profiles (Facebook, Instagram, LinkedIn, Xing).

---

## 10. Notes for the Drupal CMS migration

When this page is built in the Drupal admin, populate these Metatag module fields:

- **Title** field of the country page node, plus override the page title pattern at the node level if needed
- **Meta description** in the Metatag override section
- **Canonical** can be left to Drupal's automatic per-node behaviour once the page is live at the real URL
- **Robots** flip from noindex to `index, follow` at publication
- **Open Graph** image: upload the final hero image to the Media library and reference its public URL
- **JSON-LD**: if a structured-data module is installed (Schema.org Metatag, JSON-LD Schema, or similar), populate Organization and LocalBusiness fields. Otherwise add as a custom block on the page
