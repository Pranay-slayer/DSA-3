# Plagiarism Detection Engine for Academic Submissions

A full-stack academic plagiarism detection platform that stores uploaded documents, normalizes text, fingerprints content with Rabin-Karp + Winnowing, compares document pairs using suffix-array/LCP search, and reports similarity with match highlighting.

## Features

- Upload .txt, .docx, and .pdf documents
- Extract and normalize document text
- Generate Rabin-Karp rolling hashes
- Reduce hashes with Winnowing fingerprints
- Compare candidate pairs using suffix arrays and LCP analysis
- Calculate similarity percentages from actual content
- Highlight matching passages in a side-by-side comparison view
- Record comparisons, matches, and review decisions in SQLite via Prisma
- Dashboard and analytics pages with live corpus metrics
- Educational algorithm explainer pages for academic demonstration

## Stack

- Frontend: React + TypeScript + Vite + Tailwind CSS + React Router
- Backend: Node.js + Express + TypeScript
- Database: SQLite + Prisma
- File processing: Mammoth, pdf-parse, Multer
- Testing: Vitest, Supertest

## Folder Structure

- backend/src/algorithms
- backend/src/routes
- backend/src/services
- backend/src/utils
- backend/prisma
- frontend/src/components
- frontend/src/pages
- uploads

## Install

```bash
npm install
cd backend && npx prisma generate && npx prisma db push
```

## Run

```bash
npm run dev
```

This will run the backend and frontend together using the root workspace scripts.

## Seed sample corpus

```bash
npm run seed --workspace backend
```

## Tests

```bash
npm run test --workspace backend
```

## Known limitations

- This system detects similarity against the uploaded/local corpus only.
- It does not search the entire internet.
- Matching is heuristic and should be reviewed by an academic reviewer.
- Large PDFs may require enhancement based on the source text quality.

## Similarity calculation

The engine computes similarity as a ratio of matched characters to the maximum comparison content size for the compared pair. The result is reported as a percentage and is derived from actual document content rather than hard-coded values.

## Important notice

This system detects similarity against documents available in the uploaded/local corpus. It does not prove plagiarism and does not automatically search the entire internet.
