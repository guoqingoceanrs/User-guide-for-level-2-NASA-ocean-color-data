**Level-2 filenames and mission abbreviations**

Ocean Biology Level-2 filenames identify the mission, instrument, observation time, processing level, and product suite. Some also include a data-type identifier, geographic region, or processing version. The summary below describes the **current non-NRT files verified in CMR on October 26, 2026**.

**Common filename pattern**

Most of the reviewed files follow this pattern:

`MISSION_SENSOR[_TYPE].YYYYMMDDTHHMMSS.L2.SUITE[.VERSION].nc`

Square brackets indicate optional elements; they are not literal filename characters. This is a simplified Level-2 pattern based on the reviewed files and the OBPG naming convention.

| Element | Meaning | Examples |
|---|---|---|
| `MISSION_SENSOR` | Platform and instrument | `AQUA_MODIS`, `SNPP_VIIRS`, `PACE_OCI` |
| `_TYPE` | Optional sampling or resolution identifier | `_GAC`, `_MLAC`, `_FRS`, `_RR`, `_EFRNT` |
| `YYYYMMDDTHHMMSS` | Granule date and time: year, month, day, hour, minute, second | `20260901T235307` = September 1, 2026, 23:53:07 |
| `L2` | Level-2 processing level | `L2` |
| `SUITE` | Group of related products contained in the file | `OC`, `IOP`, `OC_AOP`, `MAPOL_OCEAN` |
| `VERSION` | Optional processing-version label | `V3_2`, `V4_0`, `V2022_0` |
| `.nc` | NetCDF filename extension | All available examples checked report netCDF-4 in CMR |

For example:

`PACE_OCI.20260901T235307.L2.OC_AOP.V3_2.nc`

identifies a PACE OCI Level-2 file in the ocean-color apparent optical properties suite, with version label 3.2.

The timestamp identifies the granule; use its metadata for the exact observation start and end times. A suite name identifies a collection of variables, rather than an individual variable such as `chlor_a`.

**Mission abbreviations: CMR names versus filenames**

CMR collection short names and filename prefixes use different abbreviations. The table maps the mission portion of the collection name to the prefixes found in the reviewed files.

| CMR mission identifier | Mission / instrument | Filename prefix |
|---|---|---|
| `CZCS` | Nimbus-7 / CZCS | `NIMBUS-7_CZCS` |
| `GOCI` | COMS / GOCI | `G` — special pattern below |
| `HAWKEYE` | SeaHawk-1 / HawkEye | `SEAHAWK1_HAWKEYE` |
| `HICO` | International Space Station / HICO | `H` — special pattern below |
| `MERIS` | Envisat / MERIS | `ENVISAT_MERIS_FRS`, `ENVISAT_MERIS_RR` |
| `MODISA` | Aqua / MODIS | `AQUA_MODIS` |
| `MODIST` | Terra / MODIS | `TERRA_MODIS` |
| `OCTS` | ADEOS-I / OCTS | `ADEOS_OCTS` |
| `OLCIS3A` | Sentinel-3A / OLCI | `S3A_OLCI_EFRNT`, `S3A_OLCI_ERRNT` |
| `OLCIS3B` | Sentinel-3B / OLCI | `S3B_OLCI_EFRNT`, `S3B_OLCI_ERRNT` |
| `SeaWiFS` | OrbView-2, also known as SeaStar / SeaWiFS | `SEASTAR_SEAWIFS_GAC`, `SEASTAR_SEAWIFS_MLAC` |
| `VIIRSN` | Suomi-NPP / VIIRS | `SNPP_VIIRS` |
| `VIIRSJ1` | NOAA-20, formerly JPSS-1 / VIIRS | `JPSS1_VIIRS` |
| `VIIRSJ2` | NOAA-21, formerly JPSS-2 / VIIRS | `JPSS2_VIIRS` |
| `PACE_OCI` | PACE / OCI | `PACE_OCI` |
| `PACE_HARP2` | PACE / HARP2 | `PACE_HARP2` |
| `PACE_SPEXONE` | PACE / SPEXone | `PACE_SPEXONE` |

The optional data-type identifiers mean:

| Identifier | Meaning |
|---|---|
| `GAC` | Global Area Coverage |
| `MLAC` | Merged Local Area Coverage |
| `FRS` | MERIS full-resolution, full-swath data |
| `RR` | MERIS reduced-resolution data |
| `EFR` / `ERR` | OLCI full-resolution / reduced-resolution data |
| `NT` in `EFRNT` or `ERRNT` | Non-time-critical processing designation |

The OLCI `NT` designation refers to non-time-critical processing; these examples belong to the non-NRT collections listed in CMR.

**Product-suite identifiers**

For non-PACE missions, the principal filename suite identifiers are:

| Suite | Meaning | Example ending |
|---|---|---|
| `OC` | Ocean color | `.L2.OC.nc` |
| `IOP` | Inherent optical properties | `.L2.IOP.nc` |
| `ILW_<REGION>` | Inland waters for a named region | `.L2.ILW_CONUS.V5.nc` |

PACE separates its products into more suites. Some CMR collection suffixes differ from the corresponding filename tokens:

| PACE sensor | CMR collection suffix | Filename suite token |
|---|---|---|
| OCI | `AOP`, `BGC`, `IOP` | `OC_AOP`, `OC_BGC`, `OC_IOP` |
| OCI | `CLOUD`, `CLOUD_MASK` | `CLD`, `CLDMASK` |
| OCI | `AER_UAA`, `UVAI_UAA` | `AER_UAA`, `UVAI_UAA` |
| OCI | `LANDVI`, `PAR`, `SFREFL`, `TRGAS` | Same as collection suffix |
| OCI | `CLOSE` | `CLOSE`, with prefix `PACE_OCI_SIM` |
| HARP2 | `CLOUD_GPC` | `CLOUD_GPC` |
| HARP2 / SPEXone | `MAPOL_LAND`, `MAPOL_OCEAN` | Same as collection suffix |
| SPEXone | `AER_RTAPLAND`, `AER_RTAPOCEAN` | `RTAP_LAND`, `RTAP_OCEAN` |

`PACE_SPEXONE_L2_MAPOL_LAND` had no indexed granules at the time of the check, so its filename pattern could not be verified from an actual file.

**Exceptions and details to preserve**

- **GOCI and HICO:** Currently archived files retain the patterns `GYYYYDDDHHMMSS.L2_COMS_OC.nc` and `HYYYYDDDHHMMSS.L2_ISS_OC.nc`, where `DDD` is the three-digit day of year. Examples are `G2021090071641.L2_COMS_OC.nc` and `H2014256113710.L2_ISS_OC.nc`.
- **Inland waters:** Region identifiers form part of the suite token, such as `ILW_CONUS` and `ILW_ALASKA`. Example: `S3A_OLCI_EFRNT.20261024T214959.L2.ILW_ALASKA.V5.nc`.
- **Version labels:** Many non-PACE filenames omit a version even though their CMR collections have one. Preserve any version token exactly as provided.
- **PACE simulations:** `PACE_OCI_SIM.20250616T011311.L2.CLOSE.v1.nc` identifies a simulation file. Its filename label `v1` differs from its CMR collection version, 3.1.
- **File contents:** Filenames support discovery and identification. Read the collection and file metadata to determine the processing version, variables, wavelengths, dimensions, units, and quality flags; these cannot all be inferred from the filename.
