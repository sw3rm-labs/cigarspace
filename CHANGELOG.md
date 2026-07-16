# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.1](https://github.com/codexofc/cigarspace/compare/v1.0.0...v1.0.1) (2026-07-16)


### Bug Fixes

* **ci:** build only the light Docker image — demo needs PG apt repo ([#36](https://github.com/codexofc/cigarspace/issues/36)) ([121f5b7](https://github.com/codexofc/cigarspace/commit/121f5b724f01baeed3d474ed84c5f42f34f03ba2))
* **ci:** omit network-tier fetchers from coverage gate; non-block frontend lint ([#33](https://github.com/codexofc/cigarspace/issues/33)) ([91ef94f](https://github.com/codexofc/cigarspace/commit/91ef94f98b45511e7f0db1c9a4d6efffea1a1754))
* **ci:** unblock CI — ruff ignore list + .npmrc for legacy peer deps ([#31](https://github.com/codexofc/cigarspace/issues/31)) ([427af35](https://github.com/codexofc/cigarspace/commit/427af3510c921678e88be7090e116b505d8948eb))
* **deps:** patch Pillow, pytest, vite, esbuild — closes 14 security alerts ([#23](https://github.com/codexofc/cigarspace/issues/23)) ([abb42a0](https://github.com/codexofc/cigarspace/commit/abb42a0b174fc777e7b37ab7bc6d94d6ef3f9236))
* **docker:** copy web/.npmrc into the build context ([#35](https://github.com/codexofc/cigarspace/issues/35)) ([9f0a2b9](https://github.com/codexofc/cigarspace/commit/9f0a2b9a58b58d8afac85810725cc0345cc3b62d))
* **lint:** sync remaining ruff --fix output to public repo ([#32](https://github.com/codexofc/cigarspace/issues/32)) ([3cc89c7](https://github.com/codexofc/cigarspace/commit/3cc89c73200bb8b730e2fa5f44f21d4ac328be94))
* **web:** vitest --passWithNoTests so empty CI doesn't fail ([#34](https://github.com/codexofc/cigarspace/issues/34)) ([0ad1e39](https://github.com/codexofc/cigarspace/commit/0ad1e39e210fce7d708c0b442bf80b5c60a47595))

## [Unreleased]

## [1.0.0] — 2026-05-25

First public release as **Cigarspace**.

### Added

- **Ingestion pipeline**: multi-merchant scraping (mistercigar.com,
  cigarpassion.ch) with a parser registry dispatching by domain.
  Resilient fetcher with tiered fallbacks (direct → HTTP proxy →
  ProtonVPN WireGuard sidecar → Tor SOCKS5).
- **Domain model**: canonical Cigar / Brand / CigarLine / Package /
  Media entities, blend components, tasting attributes, dimensions,
  flavor profile value objects.
- **Customs ingestion**: jurisdiction-neutral `CustomsSource` /
  `CustomsPublication` / `CustomsPriceEntry`. France adapter targets
  the Douane FR open-data CSV.
- **Hybrid matching**: pgvector + MPNet 768-d embeddings combined
  with trigram and structured signals via Reciprocal Rank Fusion.
  Human review queue preserves `HUMAN_*` verdicts across re-matches.
- **Public HTTP API**: FastAPI service exposing read endpoints for
  the catalogue and admin endpoints for the review queue and refresh
  jobs. OAuth2 password grant with rotating refresh tokens, RFC 7807
  errors, ETag/304, RFC 5988 pagination links, OpenAPI 3.1 generated.
- **Web admin UI**: React + Vite + TypeScript + shadcn/ui SPA with
  HttpOnly cookie auth, dashboard, cigar browser, hybrid search, and
  review queue.
- **i18n**: `react-intl` with English and French locales and an
  in-app language switcher.
- **Docker**: multi-stage `api`, `web`, and `all-in-one` images
  (light + demo variants); `docker compose` topology with Postgres
  (pgvector), Redis, SeaweedFS, optional gluetun/Tor profiles.
- **CI/CD**: GitHub Actions workflows for lint+test, multi-arch
  Docker buildx → GHCR, release-please, CodeQL, and OpenSSF Scorecard.
- **Documentation**: README with badges and Mermaid diagrams,
  architecture and data-model docs, five ADRs, deployment and
  development guides.
- **Community files**: `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`,
  `SECURITY.md`, `SUPPORT.md`, GitHub issue forms, PR template,
  CODEOWNERS, Dependabot, FUNDING.

### Licensed

- Sources distributed under **PolyForm Noncommercial 1.0.0**.
- Parallel commercial path documented in `COMMERCIAL_LICENSE.md`.

[Unreleased]: https://github.com/codexofc/cigarspace/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/codexofc/cigarspace/releases/tag/v1.0.0
