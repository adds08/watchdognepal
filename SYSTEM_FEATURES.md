# Watchdog Nepal / Simple Civic - System Features

This document outlines the core capabilities, modules, and features of the **Watchdog Nepal** (The People's Ledger) civic accountability platform. Built on Django, the system is designed to promote transparency and citizen engagement by tracking government promises against tangible actions.

## 1. Manifesto & Commitment Tracking
*   **Political Parties & Elected Members:** The system models both political parties and individual politicians. Parties can be toggled as "In Government" to highlight them on the main dashboard.
*   **Manifesto Points:** Long-term promises made by parties/members. These can be broken down into granular `SubManifesto` tasks.
*   **Commitments:** Specific, time-bound pledges. Similar to manifestos, they can be broken down into `SubCommitment` tasks.
*   **Progress Calculation:** Manifestos and Commitments automatically calculate their completion percentage (`completion_percentage`) and status (`is_completed`, `is_overdue`) based on their underlying sub-tasks and verified activities.
*   **Dynamic Deadlines:** Deadlines are tracked and highlighted with countdowns. Sub-tasks can inherit deadlines from their parent items.

## 2. Activity Feed & Crowdsourcing
*   **Citizen Submissions:** Authenticated users can submit an "Activity" (e.g., a news article, a government press release, a physical construction milestone) as evidence of progress toward a specific Manifesto or Commitment.
*   **Community Voting:** The community can upvote or downvote activities to indicate credibility.
*   **Verification:** Admins review submitted activities. Once marked "Verified," the activity officially contributes to the progress of the linked Manifesto or Commitment.
*   **Filtering & Sorting:** The Activity list can be filtered by administrative level (Federal, Provincial, Local), verification status, and sorted by newest, oldest, or highest community votes.

## 3. Petitions System
*   **Citizen Initiatives:** Authenticated users can create civic petitions with a title, description, category, and target signature goal.
*   **Signature Tracking:** Users can sign active petitions (once per petition) and leave an optional comment.
*   **Progress Goals:** The system calculates the percentage of signatures relative to the goal. Once the goal is reached, the petition is marked "Achieved."
*   **Petition States:** Petitions have lifecycle statuses: `active`, `achieved`, or `closed`.

## 4. User Dashboard
*   A personalized hub for logged-in citizens.
*   Displays the user's submitted activities, the petitions they have created, and the petitions they have signed.

## 5. Bilingual Support & Formatting
*   **Language Switcher:** Built-in Django internationalization (`i18n`). Users can switch the interface between English and Nepali.
*   **Nepali Dates:** Uses the `nepali_datetime` package to convert Gregorian deadlines and creation dates into Bikram Sambat (B.S.) formats automatically via template tags (`|to_bs`).

## 6. Security & SEO
*   **Banned IPs:** A custom `SecurityMiddleware` blocks access to users whose IP addresses are listed in the `BannedIP` admin panel.
*   **Visitor Logging:** Tracks visitor IPs, device types, browsers, OS, paths, and status codes.
*   **Dynamic Open Graph Images:** The system dynamically generates and caches custom OG images for sharing Manifestos and Commitments on social media platforms (Facebook, X/Twitter, Viber, WhatsApp).

---
*This file serves as a high-level reference for the capabilities expected to be preserved and styled when updating the application's design system.*