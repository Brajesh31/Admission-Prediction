# Frequently asked questions

## Is this a production admissions system?

No. It is an educational regression notebook and must not be used as the sole basis for admissions or other high-impact decisions.

## Does the project expose an API?

No. The current interface is the notebook's fitted model and `predict` call.

## Why is the output called an estimate?

The notebook uses regression. A numeric output is not automatically a calibrated probability and does not guarantee acceptance.

## What order should inputs use?

GRE, TOEFL, university rating, SOP rating, LOR rating, CGPA, and research experience. See [api.md](api.md).

## Where does the data come from?

The notebook reads `admission_predict.csv`. Review its provenance and license before redistributing it.

## How do I reproduce results?

Use a clean virtual environment, install the dependencies from [installation.md](installation.md), start Jupyter from the repository root, and run every cell in order.

## Can I add a new model?

Yes. Add a reproducible comparison, report metrics on an untouched test set, explain the change, and update the roadmap or README when the user-facing interpretation changes.
