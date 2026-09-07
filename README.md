# FacturIQ witness

Append-only copies of the FacturIQ registry heads (`https://api.facturiq.com/v1/checkpoint` and `/v1/attest`), written by GitHub Actions every five minutes when the registry dispatches the workflow, with an hourly backstop from GitHub's own scheduler.

Each line in `witness/YYYY-MM-DD.jsonl` records one attempt, including failed ones. A missing bucket means the scheduler did not run; a `fetch_failed` line means it ran and the registry did not answer.

`witness_sig` is an Ed25519 countersignature by this witness over `1f916.witness.v1:https://api.facturiq.com:record:<tree_size>:<root>` (same format as the 1F916 protocol, Apache-2.0). The witness public key is:

```
jG8FWfD5-wX-e13c61RPLNxZc8dcm0K67PgSKn8jyvI
```

Honest limit: this repository is controlled by the same people who run the registry. A force-push could rewrite it, loudly and detectably by anyone who ever cloned it. Clone it. Save a head. That is what closes the gap.
