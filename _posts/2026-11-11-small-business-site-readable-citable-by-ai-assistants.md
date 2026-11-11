---
layout: post
title: "How to make a small business site readable and citable by AI assistants"
description: "Structured facts, llms.txt, schema.org markup, and a consistent name, city and contact profile: a practical method for being cited by AI assistants."
date: 2026-11-11
author: Romain Bailleul
---

When a director asks an AI assistant a practical question, the assistant does not read a results page the way a person does. It gathers passages, matches them to entities it already knows, and writes an answer. You appear in that answer if your site, and the pages that talk about you, give the model facts it can lift and attribute.

This is a working method I use when I look at a small business site with that goal in mind. It has four parts that have to agree with one another: structured facts on the pages, a machine-readable map at the root of the site (`llms.txt`), schema.org markup, and a consistent name, city and contact profile (the NAP). None of the four replaces the others.

I work on this as part of [being cited in AI assistant answers](https://www.romainbailleul.fr/referencement-ia). The steps below are the part you can apply yourself.

## Write facts a model can lift

An assistant rarely cites "the page" as a whole. It cites a passage. If a key fact is spread across a headline, a metaphor and a footer, the model has to reconstruct it. Often it will skip you, or worse, it will invent the missing piece and still sound confident.

Write each important fact as a self-contained sentence: who you are, what you offer, to whom, in what form, in which city, since when, with which public proof. One idea per paragraph is enough. Dates, legal names and offers belong in the sentence, not only in an image or a slide.

State the offer in plain language. "I train teams on AI in the company, on their own files, and I advise on the framing of AI agents" can be quoted. "We support organizations in their transformation" cannot. The second sentence names no service, no public, no format. A cautious model has nothing to attribute.

Use the same wording on the home page, the about page and the service pages. Assistants build entities, not keyword clouds. If the home page uses one brand name, the about page uses another, and a directory uses a third, you look like three people. Write the public identity once (person, brand, legal name if it differs) and reuse it.

A useful test is simple. Read a paragraph out loud, without the rest of the page. If a stranger can tell what you do and for whom, the paragraph is ready to be cited. If it only makes sense after the previous section, rewrite it.

## Publish a map at the root: llms.txt

`llms.txt` is a Markdown file served at the root of the site, for example `https://www.example.com/llms.txt`. It is a proposed convention (see [llmstxt.org](https://llmstxt.org/)): a short, clean document that tells an assistant what the site is, which pages matter, and how to read them.

The file is a map, not a second website. A solid version contains:

- a short description of the organization and the site, in the same words as the public pages;
- a list of the pages you actually want cited (the pages that convert, the method pages, the about page), each with one factual line;
- the canonical site URL and a public contact path;
- optionally, a pointer to a longer `llms-full.txt` if you maintain one.

Keep the map honest. Do not list a page that does not exist. Do not claim an offer the live page does not state. Do not fill the file with slogans. When a key page changes (a new service, a new city of intervention, a change of brand wording), update `llms.txt` in the same movement as the page. A map that contradicts the site is worse than no map: it invites a confident, wrong summary.

This file does not replace the writing on the pages. Many assistants still discover you through search and through third-party sources. The map helps a model that already reaches your domain. It will not fix vague paragraphs.

## Make schema.org say the same thing as the page

JSON-LD in the page is the most reliable way to attach typed facts to your URLs: this node is a person, that node is an organization or a professional service, this URL is the official site, these profiles are the same entity.

For a small business site, a tight graph is enough:

- a `Person` node for the public face (name, job title, URL, `sameAs` profiles);
- an `Organization` or `ProfessionalService` node for the firm, linked to the person;
- stable `@id` values, reused on every page, so you do not declare the same entity twice with conflicting properties;
- `sameAs` links only to profiles you control or that already describe you (site, LinkedIn, X, GitHub, and a Wikidata item if you have one).

Two rules matter more than adding extra types. First, the markup must repeat the visible facts, not a leftover version of the offer. Second, do not declare a public `streetAddress` if you have no public office you want listed. A city and a service area are enough when you work on site at the client's premises. I live in Montpellier and I work that way. The city belongs in the graph. A street that is not a public address does not.

Conflicting markup is a frequent failure. If one page says one job title and another page says a different one, or if two nodes share a name but not an `@id`, both Google and assistants can keep the contradiction. Prefer a single source for the person and organization nodes, and let page-specific markup add only what is specific to that page.

Validate the JSON-LD with a public schema checker after each change. Validation tells you the syntax holds. It does not tell you that the facts match the page.

## Keep one NAP, everywhere it appears

NAP means name, address and phone, plus, in practice, the official URL and the public email. For a consultant without a shopfront, "address" is the city of residence and the way you intervene, not a street you do not want online.

Write the official form once and reuse it: the exact name, the brand if you use one, the city, the phone, the site, the email. That string should be identical on the site, in the schema, on the main profiles, and on any directory you still maintain. A typo in the phone, an old brand, or a second city presented as a head office is enough to split the entity.

When something changes, change it everywhere in the same week. After the change, open the main profiles and check that they still point to the same person, in the same city, with the same site.

This work looks modest, and it is the foundation the other three parts stand on. Structured paragraphs, `llms.txt` and schema.org only amplify the identity you have already stabilized.

## A workable order

Do the work in this order, so you do not decorate an identity that is still moving.

1. Freeze the public facts: person name, brand, offer in one sentence, city, phone, email, official URL.
2. Rewrite the key pages so each of those facts can be quoted on its own.
3. Align the JSON-LD with those facts, with stable `@id` values and a clean `sameAs` list.
4. Publish `llms.txt` at the root, pointing only to the pages you have just cleaned.
5. Align the main profiles with the same NAP.
6. Recheck the four parts whenever the offer, the brand wording or the contact details change.

You do not need a large publishing machine to become citable. You need a site that states who you are, what you do, for whom, and where, in a form a model can quote. Without that base, more content only gives the assistant more text to get wrong.
