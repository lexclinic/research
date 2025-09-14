# Lex.Clinic Community Memo

**Date:** September 14, 2025  
**Subject:** OAuth Identity Provider Landscape and Privy Integration

---

## 1️⃣ Executive Summary

After analyzing current identity provider (IdP) options and vendor acceptance, we have reached the following conclusions regarding Privy:

- **Privy (with GitHub as the underlying IdP)** can replace Google IdP for platforms that directly integrate Privy (e.g., Artizen Fund).  
- **Most mainstream SaaS platforms** (Slack, Notion, Figma, Shopify, etc.) do **not natively accept Privy**.  
- Until Privy(GitHub) is **universally accepted**, we must maintain **separate Google workspaces** as our Universally Accepted IdP for all mainstream apps.  
- Users will need **distinct accounts** for Google OAuth versus Privy(GitHub) OAuth on platforms without Privy support.  
- Privy is most useful for **custom apps** or platforms that explicitly integrate it, offering aggregation of multiple IdPs in a single authentication workflow.

---

## 2️⃣ Why a Single IdP is Ideal

- **Reduced Complexity:**  
  A single IdP allows a **1-to-many relationship**: 1 IdP -> many applications.  
  Fewer pointers and authentication pathways are needed, keeping system complexity low.

- **Constraint:**  
  For this to work, **all apps must accept the IdP's tokens**.  
  Currently, **only Google OAuth** is widely supported across mainstream SaaS platforms.  

- **Implication:**  
  Using Google OAuth as a single IdP enables **one login to reach most apps**, simplifying workspaces, credentials, and 2FA management.  
  Until Privy(GitHub) achieves universal vendor acceptance, **we still require separate Google workspaces** to maintain full coverage.  
  Using multiple IdPs (e.g., Google + Privy) without universal support increases operational complexity.

---

## 3️⃣ Direct IdP Acceptance Snapshot (as of September 2025)

| Platform        | Google | GitHub | Apple | Microsoft | Facebook | Privy (GitHub) |
|-----------------|--------|--------|-------|-----------|----------|----------------|
| Artizen Fund    | Yes    | Yes    | Yes   |         |          | Yes             |
| Slack           | Yes    | Yes    |       | Yes     | Yes      | No              |
| GitLab          | Yes    | Yes    |       | Yes     |          | No              |
| Figma           | Yes    | Yes    | Yes   | Yes     |          | No              |
| Shopify         | Yes    |        | Yes   | Yes     | Yes      | No              |
| Notion          | Yes    | Yes    | Yes   |         |          | No              |
| Trello          | Yes    |        | Yes   | Yes     | Yes      | No              |
| Asana           | Yes    |        | Yes   | Yes     | Yes      | No              |
| Zapier          | Yes    | Yes    | Yes   | Yes     | Yes      | No              |
| Typeform        | Yes    |        | Yes   | Yes     | Yes      | No              |
| Supabase        | Yes    |        | Yes   | Yes     | Yes      | No              |
| Clerk           | Yes    |        | Yes   | Yes     | Yes      | No              |

**Legend:**  
- **Yes** = Direct integration with this IdP  
- **No** = No direct integration

---

## 4️⃣ Recommendations

1. **Leverage Privy where supported:** Platforms like Artizen Fund can allow a switch from Google to Privy(GitHub).  
2. **Maintain separate Google workspaces for mainstream apps:** Until Privy adoption is universal, Google remains our Universally Accepted IdP.  
3. **Monitor vendor acceptance trends:** As Privy adoption grows, future consolidation of IdPs may reduce the need for multiple workspaces.

---

**Prepared for:** Lex.Clinic Community  
**Prepared by:** [bestape / Lex.Clinic Team]  
**OpenAI Session:** [https://chatgpt.com/share/68c71535-7a3c-8008-b994-506b9cbc3691](https://chatgpt.com/share/68c71535-7a3c-8008-b994-506b9cbc3691)
