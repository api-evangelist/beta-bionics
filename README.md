# Beta Bionics

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
