# RateCon Shield

**Compare the rate confirmation against the BOL, field by field, and catch the paperwork mismatch that signals double brokering. Local only. No accounts. No uploads. No server.**

RateCon Shield is a single HTML file. Open it in any browser and it works. Everything you type or paste stays in your browser's local storage on your own machine.

## The problem

Freight fraud, and double brokering in particular, is an existential risk for small carriers. A load gets re-brokered down a chain the original broker never approved, the carrier who actually hauls it never gets paid, and one bad load can put a small fleet out of business.

The classic tell is not hidden. It is sitting in the paperwork:

- The rate confirmation names one company, the bill of lading names another.
- The MC number on the load tender is not the MC number on the rate con.
- The rate on one document is not the rate on the other, because someone in the middle is skimming the difference.
- The phone, email, address or load reference changes from document to document, because the load is being kept separate from the original booking.

Those mismatches are hard to spot at 6 pm with a driver waiting. RateCon Shield lines the two documents up side by side and checks every field for you.

## What it does

- **Two structured panels.** Rate Confirmation on one side, BOL / Load Details on the other: company name, MC number, DOT number, address, phone, email, load reference, rate amount, pickup and delivery city and state.
- **Paste to extract.** Paste the raw text of a rate con email or a BOL and RateCon Shield pulls out MC numbers, DOT numbers, dollar amounts, phone numbers, emails and state / ZIP patterns. Extracted values are shown as chips for you to confirm, and they only ever fill blank fields. Your typed values are never overwritten.
- **Normalization aware comparison.** Case, punctuation, extra spaces and company suffixes (Inc, LLC, Corp) are ignored. Company name similarity is scored on token overlap, so "ABC Logistics LLC" against "ABC Logistic Inc" comes back as a caution to verify, not a silent pass and not a false alarm.
- **Risk verdict, 0 to 100.** Every field gets a Match, Caution, Mismatch or Missing status, the score is calculated from what fired, and the verdict explains, in plain language, exactly which mismatches fired and why each one matters for double brokering.
- **Red flag checklist.** Eight well known checks a document comparison cannot do: brand new broker MC, rate far above market, free email domain, booking pressure, changed factoring, pickup address that does not match the shipper, being told not to contact the shipper, and a different remittance name. Ticked flags count toward the risk picture and print in the report.
- **Printable verification report.** Both documents, the full comparison table, the flags, the verdict and the reasoning, formatted for print or PDF, with the footer "Checked locally with RateCon Shield, no data left this device".
- **Check history.** Every comparison is saved in your browser with its score and verdict. Export the history to CSV, or clear it, any time.

## Verdict bands

| Band | Meaning |
| --- | --- |
| **PASS** | Core identity fields (company, MC, DOT) agree across both documents, and nothing else material fired. |
| **CAUTION** | No fatal identity mismatch, but something needs a confirmation call before pickup: a rate, address, contact or load reference mismatch, a similar but not identical company name, a missing identity field, or ticked red flags. Caution is where most double brokering hides. |
| **FAIL** | A core identity field disagrees: company, MC number or DOT number. Two identities are in the paperwork. Do not load until the broker on the rate con confirms, on a number you already trust, why. |

## Run it

Open `index.html` in a browser. That is the whole install. Use the two demo buttons in the header to see a clean PASS and a fraud pattern FAIL in seconds.

## Honest limits

- **RateCon Shield compares what you enter or paste.** It does not verify FMCSA authority, insurance or safety records, and it does not claim to. Verifying the MC itself is what SAFER and the companion product SAFER USDOT Extractor are for. Use both: SAFER to check who a company is, RateCon Shield to check that the paperwork agrees with itself.
- **Text paste only in v1.** If your rate con is a PDF, copy the text out of it and paste. Direct PDF parsing is on the roadmap, not in this version.
- **A PASS is paperwork agreement, not a guarantee.** Determined fraud can produce consistent fake documents. The red flag checklist and a call to a known number still matter.
- **History is per browser.** Clearing browser storage clears your check history and saved inputs. Export CSV if you need a permanent record.

## Roadmap

- v1.1: saved broker profiles, so repeat brokers compare in one paste.
- v2: PDF parsing of rate cons and BOLs with local, in-browser extraction (still no uploads).
- v2: one click cross-check link out to SAFER for the MC on the documents.
- v2: shareable blank checklist mode for training new dispatchers.

## Product family

RateCon Shield is part of the Dispatch Authority toolset for carrier and dispatcher verification work:

- **SAFER USDOT Extractor**: FMCSA carrier verification and lead research.
- **Load Board Fraud Lens**: read-only fraud signals on load board postings.
- **RateCon Shield**: post-booking paperwork comparison, this tool.

Each tool covers a different point in the load lifecycle: before you book, while you browse, and after the rate con lands.

## License

MIT. See `LICENSE`. Use it, share it, and if it saves you from one bad load, tell another carrier.
