# DA-08 Toronto Library Partnership Dashboard
## Data Cleaning Decisions Log
**Project:** Toronto Public Library Partnership Dashboard
**Analyst:** [Your Name]
**Last Updated:** 2026-05-24

---

## General Rules Applied to All Tables
- All raw data kept unchanged in original variables
- All cleaning done on `.copy()` of original dataframes
- All cleaned tables saved with `_cl` suffix

---

## Table 1: `tpl_BGI_2023` → `tpl_BGI_2023_cl`
**Source:** TPL Branch General Information 2023
**Original Shape:** 112 rows, 26 columns
**Clean Shape:** 100 rows, ? columns

### Row Changes
| Decision | Reason |
|----------|--------|
| Removed 12 non-physical branches (`PhysicalBranch == 0`) | These are services not locations (e.g. Virtual Library, Automated Phone System, Bookmobile). U+ needs physical locations to run workshops. |

### Column Changes — Dropped
| Column | Reason Dropped |
|--------|---------------|
| `Address` | [Your reason] |
| `PostalCode` | Redundant with Address |
| `Lat` | [Your reason] |
| `Long` | [Your reason] |
| `WardName` | [Your reason] |
| `NBHDNo` | Redundant with NBHDName |
| `WardNo` | Redundant with WardName |
| `AdultLiteracyProgram` | Focuses on English literacy for adults 19+, not digital skills. A branch with this program is not a stronger U+ digital literacy partner than one without it. |
| `LeadingReading` | [Your reason] |
| `SquareFootage` | [Your reason] |
| `PublicParking` | Not relevant to U+ partnership scoring |
| `Website` | Manager can find this from branch name |
| `Telephone` | Not relevant to U+ partnership scoring |
| `ServiceTier` | [Your reason] |
| `PresentSiteYear` | Not relevant to U+ partnership scoring |

### Column Changes — Kept
| Column | Reason Kept |
|--------|------------|
| `BranchCode` | Primary key for joining tables |
| `BranchName` | Identifies branch for manager |
| `NBHDName` | Location context for U+ manager |
| `KidsStop` | Signals branch serves children — relevant to youth programming |
| `TeenCouncil` | Signals youth leadership already exists at branch |
| `YouthHub` | Signals branch already serves youth audience |
| `CLC` | [Your reason after investigation] |
| `DIH` | [Your reason after investigation] |
| `Workstations` | Signals digital literacy capacity |
| `TPLNIA` | Flags Neighbourhood Improvement Areas — helps U+ identify underserved communities |

---

## Table 2: `tpl_BSR_2024` → `tpl_BSR_2024_cl`
**Source:** TPL Branch Space Rentals 2024
**Original Shape:** 162 rows, 5 columns
**Clean Shape:** 86 rows (after grouping by BranchCode)

### Changes Made
| Decision | Reason |
|----------|--------|
| Grouped by BranchCode | [Your reason] |

---

## Table 3: `tpl_RABB` (Card Registrations)
**Source:** TPL Card Registrations Annual by Branch
**Original Shape:** 1275 rows, 3 columns

### Changes Made
| Decision | Reason |
|----------|--------|
| [Your cleaning steps] | [Your reasons] |

---

## Table 4: `tpl_EFS2` → `tpl_EFS2_cl` (Events)
**Source:** TPL Events Feed Source 2
**Original Shape:** 8512 rows, 16 columns

### Row Changes
| Decision | Reason |
|----------|--------|
| Removed duplicate rows (2 rows) | True duplicates add no analytical value |
| Removed Junction Triangle events | Branch does not exist in 2023 branch data — cannot be linked to a physical branch for scoring |
| Removed Junction Triangle - Closed events | Branch is closed and does not exist in branch data |
| Renamed `Daniel G. Hill` to `Jane/Dundas` | Daniel G. Hill is the renamed version of Jane/Dundas branch. Events table uses new name (2026), branch table uses old name (2023). Standardized to match 2023 branch data. |
| [Decision on nan LocationName] | [Your reason] |

### Matching Results
| Check | Count |
|-------|-------|
| Total unique location names in events | ? |
| Exact matches with branch table | 92 |
| Non-matching after fixes | 2 (Daniel G. Hill → fixed, nan → pending decision) |

---

## Table 5: `tpl_VABB` → `df_visits_agg` (Visits)
**Source:** TPL Visits Annual by Branch
**Original Shape:** 1233 rows, 3 columns
**Clean Shape:** 104 rows (after grouping by BranchCode)

### Changes Made
| Decision | Reason |
|----------|--------|
| Grouped by BranchCode, summed Visits | Need one row per branch for merging |
| 104 rows vs expected 100 | [Investigate why 4 extra branch codes exist] |

---

## Table 6: `tpl_WUABB_2018_2023` → `tpl_WUABB_2018_2023_AGG` (Workstation Usage)
**Source:** TPL Workstation Usage Annual by Branch 2018-2023
**Original Shape:** 592 rows, 3 columns

### Changes Made
| Decision | Reason |
|----------|--------|
| [Your cleaning steps] | [Your reasons] |

---

## Table 7: `tpl_LCBCT` → `tpl_LCBCT_AGG` (Circulation)
**Source:** Library Circulation by Cardholder Type
**Original Shape:** 675 rows, 4 columns

### Changes Made
| Decision | Reason |
|----------|--------|
| Grouped by Year, BranchCode, CardholderType | [Your reason] |

---

## Outstanding Issues to Resolve
- [ ] Investigate why `df_visits_agg` has 104 rows instead of 100
- [ ] Decision on `nan` LocationName rows in events table
- [ ] Confirm meaning of `CLC` and `DIH` columns
- [ ] Decide on `Lat`, `Long`, `Address` — needed for dashboard map?
- [ ] Complete aggregation of Registrations and Workstation tables

---

## Notes for Next Analyst
- Raw data preserved in original variables (no `_cl` suffix)
- Events table matched to branch table via `LocationName` → `BranchName`
- BranchCode is the primary join key for all other tables
- TPLNIA = Neighbourhood Improvement Area flag (1 = underserved area)