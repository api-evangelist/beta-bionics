# Beta Bionics

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Beta Bionics, Inc. (Nasdaq: BBNX) is a commercial-stage medical technology company that designs,
develops and commercializes the **iLet Bionic Pancreas** — an FDA-cleared automated insulin delivery
system made up of the iLet ACE Pump and the iLet Dosing Decision Software, paired with a Dexcom or
Abbott FreeStyle Libre 3 Plus continuous glucose monitor. The iLet initializes on body weight alone
and determines 100% of insulin doses without carb counting, correction factors or preset basal rates.

- https://www.betabionics.com/

## API posture

Beta Bionics is a regulated medical device manufacturer, **not an API provider**. There is no
developer program, no API documentation, no self-service registration, and no machine-readable
contract of any kind — no OpenAPI, AsyncAPI, GraphQL, protobuf, webhooks, MCP server or A2A agent
card. The 2026-08-02 enrichment pass probed every host in this profile and recorded the result.

What does exist is a **private, HIPAA-regulated cloud API** behind the clinician portal and the
iLet / Bionic Circle mobile apps:

| Surface | Host | Anonymous result |
|---|---|---|
| Bionic Portal API | `https://us-main-prod.betabionicsapi.com` | `403 {"message":"Missing Authentication Token"}` (Amazon API Gateway) |
| App API | `https://us-apps.betabionicsapi.com` | 404 |
| Users API | `https://us-users.betabionicsapi.com` | 404 |
| Bionic (HCP) Portal | `https://portal.betabionics.com/` | 200, Angular SPA |
| Identity | Amazon Cognito user pool `us-east-2_HNbbVuwO8` | OIDC discovery 200 |

## Artifacts

| Artifact | File | Method |
|---|---|---|
| Authentication | `authentication/beta-bionics-authentication.yml` | probed |
| OAuth scopes | `scopes/beta-bionics-scopes.yml` | probed |
| Well-known | `well-known/beta-bionics-well-known.yml` + `beta-bionics-openid-configuration.json` | probed |
| Conformance | `conformance/beta-bionics-conformance.yml` | searched |
| Domain security | `security/beta-bionics-domain-security.yml` | probed |
| Packages | `packages/beta-bionics-packages.yml` | searched |
| llms.txt | `llms/beta-bionics-llms.txt` | generated |

Deliberately **not** written, because the provider publishes nothing to record: `openapi/`,
`asyncapi/`, `mcp/`, `a2a/`, `skills/`, `overlays/`, `grpc/`, `errors/`, `lifecycle/`, `changelog/`,
`cli/`, `components/`, `sandbox/`, `data-model/`, and the vulnerability-disclosure / trust-center
files (both probes returned no hit).
