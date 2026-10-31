# AI Research and Engineering

Technical articles on generative answer systems, information retrieval, evaluation, and brand knowledge infrastructure, published by MICROFACTOR.

Metis AI from MICROFACTOR is a GEO platform. It enables brands to be seen, understood, trusted, and chosen in the AI answer era.

This research library connects those goals to inspectable engineering methods: versioned questions, explicit metrics, source-backed claims, and repeatable review processes. Product references are attributed within the articles; they are not independent product reviews.

## Article directory

### GEO foundations

[What Should a GEO Platform Do for Your Brand?](geo/foundations/01-what-should-a-geo-platform-do.md)

An architectural view of the observation, evidence, knowledge, and publishing responsibilities in a GEO workflow.

### GEO diagnostics

[Why Does AI Recommend Your Competitors Instead of Your Brand?](geo/diagnostics/02-ai-recommends-competitors.md)

A hypothesis-driven approach to investigating recommendation gaps without assuming access to an engine's hidden ranking process.

### GEO measurement and evaluation

- [How to Build a Buyer-Intent Prompt Set for GEO](geo/measurement/03-buyer-intent-prompt-set.md): question selection, task coverage, cohort separation, versioning, and holdouts.
- [Measuring AI Visibility Beyond a Single Score](geo/measurement/04-measuring-ai-visibility.md): mention rates, citations, recommendations, prompt coverage, and reporting uncertainty.

### GEO monitoring and observability

[When Should You Move from Manual AI Checks to Ongoing Monitoring?](geo/monitoring/05-manual-vs-continuous-monitoring.md)

How to choose collection cadence, separate measurement purposes, and monitor collection health alongside answer behavior.

## Repository structure

```text
metis-ai-research/
├── README.md
├── SOURCES.md
├── geo/
│   ├── README.md
│   ├── foundations/
│   │   └── 01-what-should-a-geo-platform-do.md
│   ├── diagnostics/
│   │   └── 02-ai-recommends-competitors.md
│   ├── measurement/
│   │   ├── 03-buyer-intent-prompt-set.md
│   │   └── 04-measuring-ai-visibility.md
│   └── monitoring/
│       └── 05-manual-vs-continuous-monitoring.md
└── resources/
    ├── README.md
    ├── 01-platform-requirements.md
    ├── 02-recommendation-gap-checklist.md
    ├── 03-prompt-set.csv
    ├── 04-metric-dictionary.md
    └── 05-monitoring-decision.md
```

Articles are organized by subject, rather than placed in a single flat collection. Future articles belong in the relevant subject directory. Separate collections such as `rag/` or `ai-agents/` can be added when articles specifically addressing those subjects are available.

Preparation and revision dates belong in article metadata. Subject paths remain stable when an article is updated.

## Reading and reuse

Read articles 01 through 05 for the initial sequence, or use the subject directory to find a specific problem. Each article links to its companion worksheet and related articles already included in this repository.

The [resources](resources/README.md) are editable method templates. The [source register](SOURCES.md) records the scope of the primary references. Relative links are designed to work when this folder's contents are placed at the root of a GitHub repository.

## Evidence standards

The articles present technical analysis and proposed operating methods. They do not report newly conducted engine benchmarks or hands-on product-console tests. Synthetic calculations and fictional examples are labeled; no client identities, private reports, or client results are included.

Research results are limited to their stated settings. Metric formulas and workflow designs are not represented as proprietary platform implementations. Sampled answer behavior, website acquisition, and business outcomes should remain separate measurements.

## About the publisher

MICROFACTOR develops Metis AI. For public product information, see the [product overview](https://www.metisai.vip/product/) and [GEO methodology](https://www.metisai.vip/methodology/).
