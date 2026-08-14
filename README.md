# Freeducation

Freeducation is a curated, open-source directory of learning resources, courses and certifications from companies and organizations across tech, broadcast, networking, media and adjacent fields.

The course catalog is no longer maintained directly in this README. The website data is the source of truth and lives in [`src/data/courses.ts`](src/data/courses.ts).

## Purpose

Freeducation helps people find useful courses that are free or accessible at low friction. Many entries are free and some include certificates, but every course is hosted by its original provider, so availability, pricing and certificate rules can change.

## Local Development

Install dependencies:

```sh
npm install
```

Start the local development server:

```sh
npm run dev
```

Build the static site:

```sh
npm run build
```

Preview a production build:

```sh
npm run preview
```

## Project Structure

```text
src/
  components/      Shared Astro components
  data/            Course and site metadata
  layouts/         Base HTML layout
  pages/           Static Astro routes
  styles/          Global visual identity and responsive styles
public/
  CNAME            GitHub Pages custom domain
```

## Course Data

Courses are defined in [`src/data/courses.ts`](src/data/courses.ts). Each entry follows this shape:

```ts
export type Course = {
  title: string;
  provider: string;
  category: string;
  topics: string[];
  language: string;
  free: boolean;
  certificate?: boolean;
  status: "available" | "coming-soon";
  description: string;
  url: string;
};
```

To add a course:

1. Add a new object to the `courses` array.
2. Use an existing provider/category when possible.
3. Add a concise description that helps search.
4. Keep the original external course URL.
5. Run `npm run build` before opening a pull request.

Categories and provider views are generated from the data automatically.

## Contributing

Contributions are welcome for:

- New free or useful courses
- Updated links
- Corrected provider metadata
- Better descriptions
- Accessibility or responsive layout improvements

Open a pull request with a short explanation of the change and, if possible, why the course belongs in the directory.

## Deployment

Freeducation is built as a static Astro site and can be deployed through GitHub Pages.

The custom domain is:

```text
freeducation.eliasschr.de
```

The root `CNAME` is kept for repository continuity, and `public/CNAME` is included so Astro copies it into the production build.

## Original Course Inventory

All course providers, course names and URLs from the previous README were migrated into [`src/data/courses.ts`](src/data/courses.ts), including Audinate, Netgear, Cisco, NDI and MA Lighting.
