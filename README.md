# CompuGlobalHyperMegaNet

> "Your Internet ads could be here!" — Homer Simpson, founder, CompuGlobalHyperMegaNet
> ([the clip](https://www.youtube.com/watch?v=9STeegpxSb0))

A **vibecoded, open-source, auditable TurboTax replacement.** Named after Homer's
internet company because that is roughly the level of corporate seriousness
involved. The tax math, however, is meant to be dead serious.

## Why

Filing a federal return with W-2s, some investments, and a mortgage should cost
zero dollars. The IRS Free File Fillable Forms are free, but they assume you
already know which number goes on which line. Commercial software knows, and
charges you for it every year. This project is the guided interview in front of
the free path.

## What it does

1. Asks you TurboTax-style gated questions ("Did you sell any stock in 2025?")
   and skips everything that does not apply to you.
2. Computes the federal return from your answers, with every rule traceable to
   a line in the IRS 1040 instructions and covered by a test.
3. Fills in the official IRS PDF forms and tells you exactly how to submit them
   yourself: print and mail, or type the numbers into Free File Fillable Forms.

It does **not** e-file on your behalf. That requires IRS software-developer
approval and annual certification, and it is out of scope for now.

## Status

Very early. The engine and PDF output are inherited from
[UsTaxes](https://github.com/ustaxes/UsTaxes) (see below). The guided interview
and the backtesting harness are being built on top.

Roadmap, roughly in order:

- [ ] Guided interview layer (gated questions per topic) for tax year 2025
- [ ] "How to file this yourself" walkthrough with mailing addresses and
      Free File Fillable Forms line mapping
- [ ] Backtesting harness: feed in prior-year returns, diff every 1040 line
      against what this produces
- [ ] Earlier tax years (2020–2024) through the same interview
- [ ] 1099 / self-employment income
- [ ] State returns

## Scope

Targets individual and married-filing-jointly filers with:

- W-2 wages
- Interest and dividends (1099-INT, 1099-DIV)
- Investment sales (1099-B, Schedule D, Form 8949)
- Mortgage interest and other itemized deductions (Schedule A)
- Rental real estate (Schedule E)
- Child tax credit, earned income credit

## Running it

```sh
nvm use
npm ci
npm start        # local web app on http://localhost:3000
npm test
```

All data stays in your browser. Nothing is sent anywhere.

## Vibecoded, you say?

Yes. The interview layer and tooling are being written with Claude Code,
by a person who has paid Intuit roughly $1,500 over the last decade and
is done with that. Every rule is still tested against IRS instructions and
real prior-year returns. "Vibecoded" describes the process, not the
standard of correctness. Read the code, run the tests, file issues.

## Disclaimer

This is not tax advice and nobody involved is a tax professional. You are
responsible for what you submit to the IRS. Check the output against the
IRS instructions before you file.

## Credit and license

This repository is a fork of [UsTaxes](https://github.com/ustaxes/UsTaxes),
an open-source federal tax application maintained by volunteers since 2020.
The tax engine, form definitions, and PDF filling are their work. The original
README is preserved at [docs/UPSTREAM_README.md](docs/UPSTREAM_README.md).

Licensed under the GNU Affero General Public License v3.0, same as upstream.
See [LICENSE](LICENSE).
