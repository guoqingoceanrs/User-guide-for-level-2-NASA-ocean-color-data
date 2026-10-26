OB_CLOUD Level-2 formats and non-PACE OC/IOP variable comparison
CMR check: 26 October 2026.
Conclusions
- The current satellite Level-2 collections checked under provider OB_CLOUD are distributed as netCDF-4. Of 100 collection/version records, 99 explicitly declare netCDF-4. HAWKEYE_L2_OC declares only netCDF at collection level, but its sampled granule declares netCDF-4 and the mission data paper confirms NetCDF4 packaging.
- The 100 records represent 90 unique short names: 54 non-NRT and 36 NRT. This corrects the earlier reported 50/40 split; the earlier 90-name list was correct.
- Non-PACE OC suites do not have identical variable inventories. IOP suites share a consistent set of product families, but exact names and counts vary with wavelengths.
- OCTS also offers both OC and IOP. CZCS, GOCI, HawkEye and HICO offer OC only in this inventory. MERIS and OLCI additionally offer ILW.
- All 50 non-PACE OC/IOP collection inventories were retrieved completely: 18 non-NRT OC, 14 non-NRT IOP, and 18 NRT counterparts. HICO's 73 associated variables required two result pages. There are 1,088 variable associations across these queries, not 1,088 unique scientific quantities.
- All returned associated variables have two spatial axes, number_of_lines and pixels_per_line, and paths under geophysical_data. These CMR associations do not enumerate every navigation, scan, band-parameter or provenance field in the binary files.
File-format evidence and scope
Query filters were provider=OB_CLOUD and processing_level_id=2. Both pages of the 100-record result were retrieved, and concept IDs were checked for uniqueness. No temporal or geographic filter was applied. No filter requiring nonzero granule counts was applied; this is a collection metadata inventory, not a guarantee of current granules in every record.

HawkEye sampled granule: G3189671888-OB_CLOUD, file SEAHAWK1_HAWKEYE.20231025T151600.L2.OC.V2022_0.nc, data_format=netCDF-4. The mission data paper independently confirms NetCDF4 packaging.

The format conclusion applies to these satellite collections in OB_CLOUD, including PACE and ILW. It is not an assertion about every historical file or all OB holdings, such as SeaBASS/in situ records. An additional broad OB_DAAC query returned in situ campaign records, illustrating why provider and product scope matter. Binary files were not downloaded or exhaustively validated.
Non-PACE suite comparison
Counts below are associated geophysical variables, including quality/diagnostic fields. They are not total variables in an entire netCDF file. A dash means no IOP collection in this inventory.
Mission/product family	OC variables	Rrs fields	IOP variables	Other OC fields beyond the shared core
MODIS Aqua / Terra	20	10	30	ipar, nflh, par, pic, poc
VIIRS Suomi-NPP	13	5	20	par, pic, poc
VIIRS NOAA-20 / NOAA-21	13	5	20	par, pic, poc
OLCI Sentinel-3A/B, EFR/ERR	16	11	32	None
MERIS FRS / RR	17	9	28	par, pic, poc
SeaWiFS GAC / MLAC	14	6	22	par, pic, poc
OCTS	14	6	22	par, pic, poc
CZCS	9	4	—	None
GOCI	13	6	—	chl_ocx, poc
HawkEye	13	6	—	pic, poc
HICO	73	65	—	chl_ocx, pic, poc


The shared OC core consists of four exact names—chlor_a, Kd_490, angstrom, l2_flags—plus the wavelength-dependent families Rrs_λ and aot_λ. No single Rrs wavelength-name is shared by every OC inventory. For example, MODIS has Rrs_443, NOAA-20/21 VIIRS has Rrs_445, and HICO has Rrs_444. Aerosol optical thickness suffixes also differ.

The IOP inventories follow a common pattern: a_λ and bb_λ at each product wavelength, plus adg_λr, aph_λr, bbp_λr and their three uncertainty fields; adg_s, bbp_s, rrsdiff and l2_flags. The reference wavelength λr is 445 nm for NOAA-20/21 VIIRS and 443 nm for the other IOP inventories. Thus each inventory has 2N + 10 fields, where N is its number of a/bb wavelengths. The metadata describe the optical retrievals as GIOP products. This common pattern does not make different wavelength fields numerically or scientifically interchangeable.
Inventories that match exactly by variable name
Within each suite separately, the following groups have identical associated variable-name sets:
- MODIS Aqua and Terra.
- VIIRS NOAA-20 and NOAA-21; Suomi-NPP has different wavelengths.
- OLCI Sentinel-3A and Sentinel-3B, EFR and ERR.
- MERIS FRS and RR.
- SeaWiFS GAC and MLAC.
All 18 available non-PACE OC/IOP NRT counterparts match their non-NRT inventory by variable name. Stored data types, units, scale/offset and spatial dimension names/order also match in these associated records. This does not establish identical calibration, algorithms, pixel values, quality or sampling. Dimension sizes were excluded from this equality test because granule sizes can vary.
Suggested wording for the user guide
The satellite Level-2 products covered by this guide are distributed in netCDF-4 format. Non-PACE OC and IOP suites use a common organization and related product families, but their exact variable inventories and wavelength-specific names depend on the instrument. OC suites contain a shared core plus sensor-dependent products; IOP suites follow a common optical-property pattern with sensor-dependent spectral bands and reference wavelengths. Always inspect the selected file's variable names, dimensions and attributes.

Exact non-NRT inventories from CMR
The following lists use variable basenames; every listed variable has the group prefix geophysical_data/. CMR variable lists are metadata associations rather than a complete ncdump.
CZCS_L2_OC
- CZCS_L2_OC, version 2022.0
Kd_490, Rrs_443, Rrs_520, Rrs_550, Rrs_670, angstrom, aot_670, chlor_a, l2_flags
GOCI_L2_OC
- GOCI_L2_OC, version 2014.0
Kd_490, Rrs_412, Rrs_443, Rrs_490, Rrs_555, Rrs_660, Rrs_680, angstrom, aot_865, chl_ocx, chlor_a, l2_flags, poc
HAWKEYE_L2_OC
- HAWKEYE_L2_OC, version 2022.0
Kd_490, Rrs_412, Rrs_447, Rrs_488, Rrs_510, Rrs_556, Rrs_670, angstrom, aot_867, chlor_a, l2_flags, pic, poc
HICO_L2_OC
- HICO_L2_OC, version 2018.0
Kd_490, Rrs_353, Rrs_358, Rrs_364, Rrs_370, Rrs_375, Rrs_381, Rrs_387, Rrs_393, Rrs_398, Rrs_404, Rrs_410, Rrs_416, Rrs_421, Rrs_427, Rrs_433, Rrs_438, Rrs_444, Rrs_450, Rrs_456, Rrs_461, Rrs_467, Rrs_473, Rrs_479, Rrs_484, Rrs_490, Rrs_496, Rrs_501, Rrs_507, Rrs_513, Rrs_519, Rrs_524, Rrs_530, Rrs_536, Rrs_542, Rrs_547, Rrs_553, Rrs_559, Rrs_564, Rrs_570, Rrs_576, Rrs_582, Rrs_587, Rrs_593, Rrs_599, Rrs_605, Rrs_610, Rrs_616, Rrs_622, Rrs_627, Rrs_633, Rrs_639, Rrs_645, Rrs_650, Rrs_656, Rrs_662, Rrs_668, Rrs_673, Rrs_679, Rrs_685, Rrs_690, Rrs_696, Rrs_702, Rrs_708, Rrs_713, Rrs_719, angstrom, aot_868, chl_ocx, chlor_a, l2_flags, pic, poc
MERIS_L2_FRS_IOP / MERIS_L2_RR_IOP
- MERIS_L2_FRS_IOP, version 2022.0
- MERIS_L2_RR_IOP, version 2022.0
a_413, a_443, a_490, a_510, a_560, a_620, a_665, a_681, a_709, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_413, bb_443, bb_490, bb_510, bb_560, bb_620, bb_665, bb_681, bb_709, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
MERIS_L2_FRS_OC / MERIS_L2_RR_OC
- MERIS_L2_FRS_OC, version 2022.0
- MERIS_L2_RR_OC, version 2022.0
Kd_490, Rrs_413, Rrs_443, Rrs_490, Rrs_510, Rrs_560, Rrs_620, Rrs_665, Rrs_681, Rrs_709, angstrom, aot_865, chlor_a, l2_flags, par, pic, poc
MODISA_L2_IOP / MODIST_L2_IOP
- MODISA_L2_IOP, version 2022.0
- MODIST_L2_IOP, version 2022.0
a_412, a_443, a_469, a_488, a_531, a_547, a_555, a_645, a_667, a_678, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_412, bb_443, bb_469, bb_488, bb_531, bb_547, bb_555, bb_645, bb_667, bb_678, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
MODISA_L2_OC / MODIST_L2_OC
- MODISA_L2_OC, version 2022.0
- MODIST_L2_OC, version 2022.0
Kd_490, Rrs_412, Rrs_443, Rrs_469, Rrs_488, Rrs_531, Rrs_547, Rrs_555, Rrs_645, Rrs_667, Rrs_678, angstrom, aot_869, chlor_a, ipar, l2_flags, nflh, par, pic, poc
OCTS_L2_IOP
- OCTS_L2_IOP, version 2022.0
a_412, a_443, a_490, a_516, a_565, a_667, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_412, bb_443, bb_490, bb_516, bb_565, bb_667, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
OCTS_L2_OC
- OCTS_L2_OC, version 2022.0
Kd_490, Rrs_412, Rrs_443, Rrs_490, Rrs_516, Rrs_565, Rrs_667, angstrom, aot_862, chlor_a, l2_flags, par, pic, poc
OLCIS3A_L2_EFR_IOP / OLCIS3A_L2_ERR_IOP / OLCIS3B_L2_EFR_IOP / OLCIS3B_L2_ERR_IOP
- OLCIS3A_L2_EFR_IOP, version 2022.0
- OLCIS3A_L2_ERR_IOP, version 2022.0
- OLCIS3B_L2_EFR_IOP, version 2022.0
- OLCIS3B_L2_ERR_IOP, version 2022.0
a_400, a_412, a_443, a_490, a_510, a_560, a_620, a_665, a_674, a_681, a_709, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_400, bb_412, bb_443, bb_490, bb_510, bb_560, bb_620, bb_665, bb_674, bb_681, bb_709, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
OLCIS3A_L2_EFR_OC / OLCIS3A_L2_ERR_OC / OLCIS3B_L2_EFR_OC / OLCIS3B_L2_ERR_OC
- OLCIS3A_L2_EFR_OC, version 2022.0
- OLCIS3A_L2_ERR_OC, version 2022.0
- OLCIS3B_L2_EFR_OC, version 2022.0
- OLCIS3B_L2_ERR_OC, version 2022.0
Kd_490, Rrs_400, Rrs_412, Rrs_443, Rrs_490, Rrs_510, Rrs_560, Rrs_620, Rrs_665, Rrs_674, Rrs_681, Rrs_709, angstrom, aot_865, chlor_a, l2_flags
SeaWiFS_L2_GAC_IOP / SeaWiFS_L2_MLAC_IOP
- SeaWiFS_L2_GAC_IOP, version 2022.0
- SeaWiFS_L2_MLAC_IOP, version 2022.0
a_412, a_443, a_490, a_510, a_555, a_670, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_412, bb_443, bb_490, bb_510, bb_555, bb_670, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
SeaWiFS_L2_GAC_OC / SeaWiFS_L2_MLAC_OC
- SeaWiFS_L2_GAC_OC, version 2022.0
- SeaWiFS_L2_MLAC_OC, version 2022.0
Kd_490, Rrs_412, Rrs_443, Rrs_490, Rrs_510, Rrs_555, Rrs_670, angstrom, aot_865, chlor_a, l2_flags, par, pic, poc
VIIRSJ1_L2_IOP / VIIRSJ2_L2_IOP
- VIIRSJ1_L2_IOP, version 2022.0
- VIIRSJ2_L2_IOP, version 2025.0
a_411, a_445, a_489, a_556, a_667, adg_445, adg_s, adg_unc_445, aph_445, aph_unc_445, bb_411, bb_445, bb_489, bb_556, bb_667, bbp_445, bbp_s, bbp_unc_445, l2_flags, rrsdiff
VIIRSJ1_L2_OC / VIIRSJ2_L2_OC
- VIIRSJ1_L2_OC, version 2022.0
- VIIRSJ2_L2_OC, version 2025.0
Kd_490, Rrs_411, Rrs_445, Rrs_489, Rrs_556, Rrs_667, angstrom, aot_868, chlor_a, l2_flags, par, pic, poc
VIIRSN_L2_IOP
- VIIRSN_L2_IOP, version 2022.0
a_410, a_443, a_486, a_551, a_671, adg_443, adg_s, adg_unc_443, aph_443, aph_unc_443, bb_410, bb_443, bb_486, bb_551, bb_671, bbp_443, bbp_s, bbp_unc_443, l2_flags, rrsdiff
VIIRSN_L2_OC
- VIIRSN_L2_OC, version 2022.0
Kd_490, Rrs_410, Rrs_443, Rrs_486, Rrs_551, Rrs_671, angstrom, aot_862, chlor_a, l2_flags, par, pic, poc
NRT counterparts checked
- MODISA_L2_IOP_NRT: same variable-name inventory as MODISA_L2_IOP.
- MODISA_L2_OC_NRT: same variable-name inventory as MODISA_L2_OC.
- MODIST_L2_IOP_NRT: same variable-name inventory as MODIST_L2_IOP.
- MODIST_L2_OC_NRT: same variable-name inventory as MODIST_L2_OC.
- OLCIS3A_L2_EFR_IOP_NRT: same variable-name inventory as OLCIS3A_L2_EFR_IOP.
- OLCIS3A_L2_EFR_OC_NRT: same variable-name inventory as OLCIS3A_L2_EFR_OC.
- OLCIS3A_L2_ERR_IOP_NRT: same variable-name inventory as OLCIS3A_L2_ERR_IOP.
- OLCIS3A_L2_ERR_OC_NRT: same variable-name inventory as OLCIS3A_L2_ERR_OC.
- OLCIS3B_L2_EFR_IOP_NRT: same variable-name inventory as OLCIS3B_L2_EFR_IOP.
- OLCIS3B_L2_EFR_OC_NRT: same variable-name inventory as OLCIS3B_L2_EFR_OC.
- OLCIS3B_L2_ERR_IOP_NRT: same variable-name inventory as OLCIS3B_L2_ERR_IOP.
- OLCIS3B_L2_ERR_OC_NRT: same variable-name inventory as OLCIS3B_L2_ERR_OC.
- VIIRSJ1_L2_IOP_NRT: same variable-name inventory as VIIRSJ1_L2_IOP.
- VIIRSJ1_L2_OC_NRT: same variable-name inventory as VIIRSJ1_L2_OC.
- VIIRSJ2_L2_IOP_NRT: same variable-name inventory as VIIRSJ2_L2_IOP.
- VIIRSJ2_L2_OC_NRT: same variable-name inventory as VIIRSJ2_L2_OC.
- VIIRSN_L2_IOP_NRT: same variable-name inventory as VIIRSN_L2_IOP.
- VIIRSN_L2_OC_NRT: same variable-name inventory as VIIRSN_L2_OC.
Complete collection-format audit
Collection short name	Version	CMR format	CMR record
CZCS_L2_OC	2022.0	netCDF-4	C3300838564-OB_CLOUD
GOCI_L2_OC	2014.0	netCDF-4	C3558858528-OB_CLOUD
HAWKEYE_L2_OC	2022.0	netCDF	C3160685780-OB_CLOUD
HICO_L2_OC	2018.0	netCDF-4	C3555970700-OB_CLOUD
MERIS_L2_FRS_IOP	2022.0	netCDF-4	C3281901057-OB_CLOUD
MERIS_L2_FRS_OC	2022.0	netCDF-4	C3281778845-OB_CLOUD
MERIS_L2_ILW	5.0	netCDF-4	C3433948159-OB_CLOUD
MERIS_L2_RR_IOP	2022.0	netCDF-4	C3281901072-OB_CLOUD
MERIS_L2_RR_OC	2022.0	netCDF-4	C3281778850-OB_CLOUD
MODISA_L2_IOP	2022.0	netCDF-4	C3380708974-OB_CLOUD
MODISA_L2_IOP_NRT	2022.0	netCDF-4	C3380708971-OB_CLOUD
MODISA_L2_OC	2022.0	netCDF-4	C3380708980-OB_CLOUD
MODISA_L2_OC_NRT	2022.0	netCDF-4	C3380708978-OB_CLOUD
MODIST_L2_IOP	2022.0	netCDF-4	C3384236975-OB_CLOUD
MODIST_L2_IOP_NRT	2022.0	netCDF-4	C3384236974-OB_CLOUD
MODIST_L2_OC	2022.0	netCDF-4	C3384236979-OB_CLOUD
MODIST_L2_OC_NRT	2022.0	netCDF-4	C3384236977-OB_CLOUD
OCTS_L2_IOP	2022.0	netCDF-4	C3300834690-OB_CLOUD
OCTS_L2_OC	2022.0	netCDF-4	C3300834711-OB_CLOUD
OLCIS3A_L2_EFR_IOP	2022.0	netCDF-4	C3406446181-OB_CLOUD
OLCIS3A_L2_EFR_IOP_NRT	2022.0	netCDF-4	C3406446161-OB_CLOUD
OLCIS3A_L2_EFR_OC	2022.0	netCDF-4	C3406446219-OB_CLOUD
OLCIS3A_L2_EFR_OC_NRT	2022.0	netCDF-4	C3406446207-OB_CLOUD
OLCIS3A_L2_ERR_IOP	2022.0	netCDF-4	C3406446278-OB_CLOUD
OLCIS3A_L2_ERR_IOP_NRT	2022.0	netCDF-4	C3406446252-OB_CLOUD
OLCIS3A_L2_ERR_OC	2022.0	netCDF-4	C3406446332-OB_CLOUD
OLCIS3A_L2_ERR_OC_NRT	2022.0	netCDF-4	C3406446308-OB_CLOUD
OLCIS3A_L2_ILW	5.0	netCDF-4	C3433948389-OB_CLOUD
OLCIS3B_L2_EFR_IOP	2022.0	netCDF-4	C3407754937-OB_CLOUD
OLCIS3B_L2_EFR_IOP_NRT	2022.0	netCDF-4	C3407754902-OB_CLOUD
OLCIS3B_L2_EFR_OC	2022.0	netCDF-4	C3407754974-OB_CLOUD
OLCIS3B_L2_EFR_OC_NRT	2022.0	netCDF-4	C3407754966-OB_CLOUD
OLCIS3B_L2_ERR_IOP	2022.0	netCDF-4	C3407754995-OB_CLOUD
OLCIS3B_L2_ERR_IOP_NRT	2022.0	netCDF-4	C3407754982-OB_CLOUD
OLCIS3B_L2_ERR_OC	2022.0	netCDF-4	C3407755020-OB_CLOUD
OLCIS3B_L2_ERR_OC_NRT	2022.0	netCDF-4	C3407754999-OB_CLOUD
OLCIS3B_L2_ILW	5.0	netCDF-4	C3433948481-OB_CLOUD
PACE_HARP2_L2_CLOUD_GPC	3.0	netCDF-4	C3600169991-OB_CLOUD
PACE_HARP2_L2_CLOUD_GPC	4.0	netCDF-4	C4126552781-OB_CLOUD
PACE_HARP2_L2_CLOUD_GPC_NRT	3.0	netCDF-4	C3600169974-OB_CLOUD
PACE_HARP2_L2_CLOUD_GPC_NRT	4.0	netCDF-4	C4126552646-OB_CLOUD
PACE_HARP2_L2_MAPOL_LAND	4.0	netCDF-4	C4126558424-OB_CLOUD
PACE_HARP2_L2_MAPOL_LAND_NRT	4.0	netCDF-4	C4126558421-OB_CLOUD
PACE_HARP2_L2_MAPOL_OCEAN	3.0	netCDF-4	C3652817390-OB_CLOUD
PACE_HARP2_L2_MAPOL_OCEAN	4.0	netCDF-4	C4126580712-OB_CLOUD
PACE_HARP2_L2_MAPOL_OCEAN_NRT	3.0	netCDF-4	C3652817338-OB_CLOUD
PACE_HARP2_L2_MAPOL_OCEAN_NRT	4.0	netCDF-4	C4126576758-OB_CLOUD
PACE_OCI_L2_AER_UAA	3.1	netCDF-4	C3620139465-OB_CLOUD
PACE_OCI_L2_AER_UAA_NRT	3.1	netCDF-4	C3620139326-OB_CLOUD
PACE_OCI_L2_AOP	3.2	netCDF-4	C4124887023-OB_CLOUD
PACE_OCI_L2_AOP_NRT	3.2	netCDF-4	C4124887001-OB_CLOUD
PACE_OCI_L2_BGC	3.2	netCDF-4	C4124887072-OB_CLOUD
PACE_OCI_L2_BGC_NRT	3.2	netCDF-4	C4124887054-OB_CLOUD
PACE_OCI_L2_CLOSE	3.1	netCDF-4	C4263376617-OB_CLOUD
PACE_OCI_L2_CLOUD	3.1	netCDF-4	C3620139813-OB_CLOUD
PACE_OCI_L2_CLOUD_MASK	3.1	netCDF-4	C3620139782-OB_CLOUD
PACE_OCI_L2_CLOUD_MASK_NRT	3.1	netCDF-4	C3620139761-OB_CLOUD
PACE_OCI_L2_CLOUD_NRT	3.1	netCDF-4	C3620139797-OB_CLOUD
PACE_OCI_L2_IOP	3.2	netCDF-4	C4124887265-OB_CLOUD
PACE_OCI_L2_IOP_NRT	3.2	netCDF-4	C4124887231-OB_CLOUD
PACE_OCI_L2_LANDVI	3.1	netCDF-4	C3620139839-OB_CLOUD
PACE_OCI_L2_LANDVI_NRT	3.1	netCDF-4	C3620139833-OB_CLOUD
PACE_OCI_L2_PAR	3.2	netCDF-4	C4124887997-OB_CLOUD
PACE_OCI_L2_PAR_NRT	3.2	netCDF-4	C4124887982-OB_CLOUD
PACE_OCI_L2_SFREFL	3.1	netCDF-4	C3620139902-OB_CLOUD
PACE_OCI_L2_SFREFL_NRT	3.1	netCDF-4	C3620139865-OB_CLOUD
PACE_OCI_L2_TRGAS	3.0	netCDF-4	C3993527322-OB_CLOUD
PACE_OCI_L2_TRGAS_NRT	3.0	netCDF-4	C3993527307-OB_CLOUD
PACE_OCI_L2_UVAI_UAA	3.1	netCDF-4	C3620139979-OB_CLOUD
PACE_OCI_L2_UVAI_UAA_NRT	3.1	netCDF-4	C3620139932-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPLAND	3.0	netCDF-4	C3555839907-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPLAND	4.0	netCDF-4	C4126554461-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPLAND_NRT	3.0	netCDF-4	C3555839744-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPLAND_NRT	4.0	netCDF-4	C4126554445-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPOCEAN	3.0	netCDF-4	C3555840220-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPOCEAN	4.0	netCDF-4	C4126554526-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPOCEAN_NRT	3.0	netCDF-4	C3555840000-OB_CLOUD
PACE_SPEXONE_L2_AER_RTAPOCEAN_NRT	4.0	netCDF-4	C4126554489-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_LAND	4.0	netCDF-4	C4126583126-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_LAND_NRT	4.0	netCDF-4	C4126583006-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_OCEAN	3.0	netCDF-4	C3652817426-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_OCEAN	4.0	netCDF-4	C4126583208-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_OCEAN_NRT	3.0	netCDF-4	C3652817414-OB_CLOUD
PACE_SPEXONE_L2_MAPOL_OCEAN_NRT	4.0	netCDF-4	C4126583180-OB_CLOUD
SeaWiFS_L2_GAC_IOP	2022.0	netCDF-4	C3198658845-OB_CLOUD
SeaWiFS_L2_GAC_OC	2022.0	netCDF-4	C2789774382-OB_CLOUD
SeaWiFS_L2_MLAC_IOP	2022.0	netCDF-4	C3198658953-OB_CLOUD
SeaWiFS_L2_MLAC_OC	2022.0	netCDF-4	C3198658688-OB_CLOUD
VIIRSJ1_L2_IOP	2022.0	netCDF-4	C3396928893-OB_CLOUD
VIIRSJ1_L2_IOP_NRT	2022.0	netCDF-4	C3396928892-OB_CLOUD
VIIRSJ1_L2_OC	2022.0	netCDF-4	C3396928899-OB_CLOUD
VIIRSJ1_L2_OC_NRT	2022.0	netCDF-4	C3396928895-OB_CLOUD
VIIRSJ2_L2_IOP	2025.0	netCDF-4	C3779578076-OB_CLOUD
VIIRSJ2_L2_IOP_NRT	2025.0	netCDF-4	C3779577977-OB_CLOUD
VIIRSJ2_L2_OC	2025.0	netCDF-4	C3779578213-OB_CLOUD
VIIRSJ2_L2_OC_NRT	2025.0	netCDF-4	C3779578158-OB_CLOUD
VIIRSN_L2_IOP	2022.0	netCDF-4	C3388381176-OB_CLOUD
VIIRSN_L2_IOP_NRT	2022.0	netCDF-4	C3388381223-OB_CLOUD
VIIRSN_L2_OC	2022.0	netCDF-4	C3388381264-OB_CLOUD
VIIRSN_L2_OC_NRT	2022.0	netCDF-4	C3388381281-OB_CLOUD
