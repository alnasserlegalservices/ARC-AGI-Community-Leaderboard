# MERENVAY–Mentova Runtime Repair

## Result reported

A native symbolic solver reproduced **120/120 exact tasks (100.00%)** on the ARC-AGI-2 **public evaluation set** across independent executions and two operating systems:

- Windows x64 / SWI-Prolog 10.0.2 — run 1: **120/120**, 78.185 s, failures `[]`
- Windows x64 / SWI-Prolog 10.0.2 — run 2: **120/120**, 78.442 s, failures `[]`
- GitHub-hosted Ubuntu 24.04.5 / SWI-Prolog 9.0.4: **120/120**, 40.412 s, failures `[]`

## Contribution

The pinned upstream Mentova source is commit `d117c699416692cac7ceb951b09f2cdb484a89a6`.

The upstream dispatcher could reach correct, already-existing rules too late under its 10-second per-task limit. The MERENVAY patch moves six verified rules earlier using narrow O(cells) structural prefilters:

- `mirror_patch`
- `template_expand`
- `constellation`
- `mosaic_heal`
- `hole_color`
- `frame_compass`

The patch does **not** add answer keys, alter task data, or change transformation semantics. The contribution is a bounded runtime-stability and dispatch-order repair plus an independently recorded cross-platform reproduction.

## Public evidence

- Code and reproduction instructions: https://github.com/alnasserlegalservices/merenvay-arc2-public-reproduction
- Stable GitHub Actions run: https://github.com/alnasserlegalservices/merenvay-arc2-public-reproduction/actions/runs/37769412232
- Evidence artifact: https://github.com/alnasserlegalservices/merenvay-arc2-public-reproduction/actions/runs/37769412232/artifacts/11547158323
- GitHub SLSA/Sigstore attestation: https://github.com/alnasserlegalservices/merenvay-arc2-public-reproduction/attestations/53909570
- Rekor transparency-log entry: https://search.sigstore.dev?logIndex=3147098838
- Detailed stable receipt: https://github.com/alnasserlegalservices/merenvay-arc2-public-reproduction/blob/main/STABLE_VERIFICATION_RECEIPT.md

The GitHub-hosted workflow performs a clean checkout, pins the upstream commit, applies the public patch, executes all 120 tasks, asserts `RESULT score=120 total=120`, asserts `FAILS []`, uploads the evidence artifact and generates signed build provenance.

## Evidence fingerprints

- GitHub artifact service digest: `sha256:da6a5d98a745c6f5fcad6d5a7a01b54f2b4e97f3c27279e8c873281ba7ead37b`
- Inner GitHub evidence ZIP SHA-256: `b79224b93df193dc9454be4b74eb5d3f1e752624c93291fbd8855cb1ee6f0bd1`
- GitHub run-log SHA-256: `cd4f2feb3b4a13584d2d8e482c4fb2b12d476e0920266e890d38369b7874e516`
- GitHub artifact patch SHA-256: `11a330022288ce124851d70488c0f7a1efe1351d109ea39d21c2e81d9aaa065c`
- Runner SHA-256: `46516f5efd776bb19eaec1f9004a412d85104ede657a3fe5b25a4d5fec35373e`

A final local stable evidence package was also timestamped through DigiCert RFC 3161:

- Evidence ZIP SHA-256: `5aab73ee0d7bc5c53430ebfa0565b75c29206815c394792d9c4b31925c46b59f`
- Timestamp: `2026-10-08 11:24:23 GMT`
- Status: `Granted`
- Local cryptographic verification: `Verification: OK`

## Important limitations

This is a **self-reported public-evaluation result** submitted for transparent community review. It is not an ARC Prize Verified semi-private or private score, does not establish hidden-set generalisation, and is not a certificate of general intelligence.

The underlying Mentova solver was developed task-by-task against the public evaluation corpus and its published report discloses human solution walkthroughs and official-answer confirmation for difficult public tasks. Accordingly, this entry should be interpreted as a reproducible symbolic public-benchmark implementation and runtime-repair record—not as uncontaminated evidence of fluid intelligence on unseen tasks.
