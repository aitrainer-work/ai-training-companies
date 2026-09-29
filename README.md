# AI Training Companies Dataset



55 companies that pay people to train and evaluate AI models: expert networks, crowdwork platforms and data vendors. One record per company, covering how it hires, how it pays, what work it offers and what its job listings pay.

Version 2026.09, released 2026-09-29. Browse and filter it online: [AI training companies dataset on aitrainer.work](https://aitrainer.work/open-data/companies "AI training companies dataset: hiring, pay and work facts").

## Files

| File | Contents |
|---|---|
| `data/companies.json` | Every record, plus dataset notes and license |
| `data/companies.csv` | One row per company. Arrays are joined with `; `, nested objects become dotted columns (`listings.active`) |

## How it's built

Each record has two kinds of fields.

**Checked facts.** Every curated field is checked by hand against a primary source: the company's own site (about page, careers page, help centre, terms), a filing, or a news report for founding year and parent company. Headcount is the size band the company selects on its public LinkedIn page, read while logged out. The `sources` object gives the URL behind every checked field, and `last_checked` gives the date. When a company doesn't publish a fact, the field is `null`. No field is copied from a third-party directory.

**Listing statistics.** Computed from the job listings aitrainer.work has observed on each platform since tracking began on it, open and closed. These exist only for the 21 companies whose listings are tracked (`listings` is set).

## Fields

| Field | Type | Description |
|---|---|---|
| `id` | string | Stable identifier, kebab-case |
| `name` | string | Brand name |
| `website` | URL | Company homepage |
| `operator` | string or null | Parent or operating company, e.g. Outlier AI → Scale AI |
| `hq` | string or null | Headquarters as the company states it |
| `hq_country` | string or null | ISO 3166-1 alpha-2 |
| `founded` | integer or null | Year founded |
| `headcount` | string or null | LinkedIn size band, e.g. `51-200`, `10001+` |
| `work_types` | string[] | `rlhf`, `model_evaluation`, `red_teaming`, `expert_data`, `coding`, `data_labeling`, `image_video_annotation`, `audio_speech`, `data_collection`, `translation`, `content_moderation`, `research_studies` |
| `classification` | string or null | `contractor`, `employee` or `both` |
| `payout_frequency` | string or null | `weekly`, `biweekly`, `monthly`, `per_task`, `on_demand` (withdraw any time) or `varies` |
| `payment_methods` | string[] | `paypal`, `bank_transfer`, `payoneer`, `wise`, `deel`, `airtm`, `hyperwallet`, `stripe`, `crypto`, `gift_card` |
| `eligible_countries` | string or null | Free text, as the company states it |
| `hiring_steps` | string[] | `application`, `id_verification`, `assessment`, `ai_interview`, `interview`, `trial_task`, `background_check` |
| `stated_pay` | object or null | `{min, max, unit, currency}`, only as the company states it on its own site |
| `description` | string | Summary, 300 characters or fewer |
| `pros`, `cons` | string[] | Sourced facts about working there |
| `listings` | object or null | `active`, `last_90d`, `first_seen`, `last_seen` |
| `pay_observed_hourly_usd` | object or null | `{median, p25, p75, n}` from listings that state an hourly rate. Estimated rates are excluded. Shown only with 10 or more listings |
| `top_domains` | object[] | Most common fields of work in the company's listings, with counts |
| `trustpilot_sample` | object or null | `{avg_rating, reviews_sampled, url, scraped_at}`: the average of the reviews collected on `scraped_at`, which is not Trustpilot's TrustScore |
| `profile_url` | URL or null | Company profile on aitrainer.work |
| `sources` | object | Source URL for each checked field |
| `last_checked` | date | Date the record was last checked |

## Coverage in this version

| Field | Companies with a value |
|---|---|
| Companies | 55 |
| Headcount band | 52 |
| Worker classification | 32 |
| Payout frequency | 34 |
| Hiring steps | 44 |
| Payment methods | 27 |
| Eligible countries | 26 |
| Parent or operator | 18 |
| Stated pay | 17 |
| Headquarters | 15 |
| Founding year | 13 |
| Listing statistics | 21 |
| Observed hourly pay (10+ listings) | 9 |
| Trustpilot sample | 9 |

## Limitations

- The dataset covers the companies aitrainer.work tracks, not every company in the field. AI labs hiring employees and general freelance marketplaces are out of scope.
- Crowd platforms such as Outlier and OneForma pick LinkedIn size bands that appear to count contractors, so their headcount is not comparable with that of smaller firms.
- Listing statistics reflect what platforms post publicly. A company that hires mostly through invitations will show few listings.
- `trustpilot_sample` was collected in January 2026 and is not refreshed monthly.

## Updates

A new release is published each month. Each release is archived on Zenodo as a new version under one DOI, which always resolves to the latest version.

## Citation

> Romeo, P. (2026). *AI Training Companies Dataset* (version 2026.09). aitrainer.work. https://github.com/aitrainer-work/ai-training-companies

GitHub's "Cite this repository" button reads `CITATION.cff`.

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You can use, share and adapt the data for any purpose with attribution: "Data from aitrainer.work/open-data/companies, licensed under CC BY 4.0."

## Competing interests

aitrainer.work has referral agreements with some of the companies in this dataset.

## Related data

- [AI training job market statistics](https://aitrainer.work/open-data "Open data: AI training job market statistics"): pay, listing volume and hiring outcomes across the platforms aitrainer.work tracks.

Questions and corrections: research@aitrainer.work, or open an issue.
