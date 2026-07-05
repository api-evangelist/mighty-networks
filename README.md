# Mighty Networks (mighty-networks)

Mighty Networks is a community, courses, and membership platform where creators, brands, and businesses run branded networks made up of spaces, members, posts, events, courses, and paid plans. For years Mighty Networks offered only a Zapier integration and no traditional developer API. That has changed: Mighty Networks now ships a documented public **Admin API** — a REST interface (OpenAPI 3.1, base `https://api.mn.co/admin/v1`) authenticated with a long-lived Bearer API token — alongside a **beta Headless GraphQL API** for user-context clients and **40+ outbound webhook** event types.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/mighty-networks/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/mighty-networks/refs/heads/main/apis.yml)

## Access Model

- **Admin API** — REST, base `https://api.mn.co/admin/v1`, described by a public OpenAPI 3.1 document ([`api.mn.co/admin/v1/spec.json`](https://api.mn.co/admin/v1/spec.json), mirrored in [`openapi/`](openapi/mighty-networks-admin-api-openapi.json)). Authenticated with a Bearer API token from the network admin panel: `Authorization: Bearer YOUR_API_TOKEN`. 137 operations across 25 resource groups. Requires a **Scale, Growth, or Mighty Pro** plan.
- **Headless API (beta)** — GraphQL, `POST https://api.mn.co/networks/:network_id_or_subdomain/graphql`, authenticated with **OAuth 2.0** short-lived, user-context access tokens (member, moderator, or host). Powers the official Mighty Networks clients. Available on **Mighty Pro**.
- **Webhooks** — 40+ outbound event types delivered as HTTP POST callbacks (member, content, comment, reaction, course-progress, event, RSVP, poll, purchase, subscription, plan, badge, tag, and custom-field events).
- **Zapier** — the historical integration path, still available on Scale and above; the only automation option on the entry-level Launch plan.

There is **no documented public WebSocket API** — the API surface is request/response REST and GraphQL plus outbound webhooks. See [`review.yml`](review.yml).

## Tags

- Community
- Courses
- Membership
- Creator Economy
- Events
- Subscriptions

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

The ~137 real Admin API operations are grouped into 14 logical REST/webhook APIs plus the Headless GraphQL API for cataloging. Every referenced endpoint is present in the published OpenAPI document.

### Mighty Networks Members API

Create, list, get, update, ban, and remove members across a network, its spaces, and its plans. Look up members by id, email, member id, or user id, manage network and space roles, and directly add members to free plans.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/members/return-members-of-the-given-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Spaces API

Manage spaces — the organizational units that hold content and members. Create, list, get, update, and delete spaces, list a member's spaces, and organize spaces into collections.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/spaces/returns-a-list-of-spaces-for-the-current-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Posts API

Create, list, get, update, and delete posts and articles across the network, optionally notifying members when new content is published.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/posts/returns-a-list-of-posts-for-the-current-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Comments and Reactions API

Manage engagement on content — comments on posts, reactions on posts and comments, and muting or unmuting a post for a specific user.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/comments/returns-a-list-of-comments-for-a-specific-post)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Events and RSVPs API

Create, list, get, update, and delete scheduled events, and manage the RSVPs members create against them.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/events/returns-a-paginated-list-of-events-in-the-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Courses API

Build and manage course content within a space course — create, list, get, update, and delete coursework items such as lessons, quizzes, and sections.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/courseworks/returns-a-list-of-coursework-items-for-the-given-space-course)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Plans and Subscriptions API

List and get plans, archive plans, list plan members, and manage the purchases and payment subscriptions members hold, including canceling a subscription or revoking purchase access.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/plans/return-all-plans-in-the-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Invites API

Invite people into a network or a specific plan — create and send, list, get, update, resend, revoke, and delete unaccepted invites.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/invites/returns-a-list-of-invitations-for-the-current-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Badges and Tags API

Create, update, and delete badges and tags, list them for the network, and add or remove badges and tags on individual members.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/badges/return-all-badges-for-the-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Custom Fields API

Define and collect structured member profile data — custom fields, dropdown options, and each member's answers to those fields.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/customfields/return-custom-fields-of-the-given-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Polls and Questions API

Create, list, get, update, and delete polls and questions that let members share opinions and engage with each other.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/polls/returns-a-paginated-list-of-polls-and-questions-in-the-network)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Network and Collections API

Read details of the network that owns the API key, manage collections that group spaces, upload image and file assets, and inspect the authenticated access token via the Me endpoint.

- **Base URL:** `https://api.mn.co/admin/v1`
- [API Reference](https://docs.mightynetworks.com/api-reference/networks/returns-details-of-the-network--must-match-the-network-owning-the-requesting-api-key)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Webhooks

Subscribe to 40+ outbound webhook event types delivered as HTTP POST callbacks — member joins and updates, posts and articles, comments, reactions, course progress, events and RSVPs, polls, purchases, subscriptions, plan changes, badges, tags, and custom-field responses.

- **Base URL:** `https://api.mn.co/admin/v1`
- [Documentation](https://docs.mightynetworks.com/api-reference/webhooks/memberjoined)
- [OpenAPI](openapi/mighty-networks-admin-api-openapi.json)

### Mighty Networks Headless GraphQL API

Beta GraphQL interface that powers the official Mighty Networks clients, for building custom user-context clients, integrations, and back-office tools. Requests go to `/networks/:network_id_or_subdomain/graphql` and use OAuth 2.0 short-lived access tokens acting on behalf of a specific member, moderator, or host. Available on Mighty Pro.

- **Base URL:** `https://api.mn.co/networks`
- [Documentation](https://docs.mightynetworks.com/headless-api)
- [Authentication](https://docs.mightynetworks.com/headless-authentication)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/mighty-networks)
- [Website](https://www.mightynetworks.com)
- [Documentation](https://docs.mightynetworks.com)
- [Changelog](https://docs.mightynetworks.com/admin-api-changelog)
- [Plans](plans/mighty-networks-plans-pricing.yml)
- [Rate Limits](rate-limits/mighty-networks-rate-limits.yml)
- [Fin Ops](finops/mighty-networks-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
