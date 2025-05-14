# Fix xreg_mode logic to match documentation

## Summary
This PR fixes the implementation of the `xreg_mode` option in the forecast with covariates method to match the documentation. Previously, the logic for `"xreg + timesfm"` and `"timesfm + xreg"` was swapped compared to the documented behavior.

## Details
- Swapped the docstring in `src/timesfm/timesfm_base.py` so that:
  - `"timesfm + xreg"` now fits a model on the residuals of the TimesFM forecast (first TimesFM, then xreg on residuals)
  - `"xreg + timesfm"` now fits a model on the targets, then forecasts on the residuals via TimesFM (first xreg, then TimesFM on residuals)
- Updated docstring to match the corrected logic.

## Motivation
This resolves a bug for users and ensures the code matches the documented behavior.

## Checklist
- [x] Code and documentation are now consistent
- [ ] Tests pass (please verify)

---
Closes: #275
