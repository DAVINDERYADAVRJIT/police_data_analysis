# police_data_analysis
Description of standardized data
Each row in the standardized data for each state provides information for one state patrol stop. All standardized data files contain the following columns. If a column cannot be computed using the data a state has provided, it is set to NA. Some states also have additional columns (e.g., an ID for the officer making the stop), which we do not use in our analysis, but which we include here because they might be useful to other researchers. These extra columns are explained in the state notes.

For several fields (e.g., driver_race) we include a "raw" column which records the original data values from which we infer standardized values. For example, driver_race_raw might be “White Hispanic” which we code as “Hispanic” in the standardized driver_race field. We include the raw columns because our data processing pipeline is extensive, requiring judgment calls and subjective decisions. We aim to make our data processing as transparent as possible. Other analysts may choose to process the raw data differently if their needs or judgments differ.

Column name	Column meaning	Example value
id	The unique ID we assign to each stop. Contains the state and year.	VT-2011-00012
state	The two-letter code for the state in which the stop occurred.	VT
stop_date	The date of the stop, in YYYY-MM-DD format. Some states do not provide the exact stop date: for example, they only provide the year or quarter in which the stop occurred. For these states, stop_date is set to the date at the beginning of the period: for example, January 1 if only year is provided.	2011-11-27
stop_time	The 24-hour time of the stop, in HH:MM format.	20:15
location_raw	The original data value from which we compute the county (or comparably granular location) in which the stop occurred. Not in a standardized format across states.	Winooski
county_name	The standardized name of the county in which the stop occurred.	Chittenden County
county_fips	The standardized 5-digit FIPS code in which the stop occurred.	50007
district	In several states (e.g., Illinois) the stop county cannot be inferred, but a comparably granular location can. This comparably granular location is stored in the district column. Most states do not have this column.	ILLINOIS STATE POLICE 01
fine_grained_location	Any higher-resolution data about where the stop occurred: e.g., milepost or address. Not standardized across states.	90400 I 89 N; EXIT 15 MM90/40
police_department	The police department or agency that made the stop. Not in a standard format across states.	WILLISTON VSP
driver_gender	The driver’s gender, as recorded by the trooper. M, F, or NA.	M
driver_age_raw	The original data value from which we compute the driver’s age when they were stopped. May be age, birth year, or birth date. Not in a standard format across states.	1988
driver_age	The driver’s age when they were stopped. Set to NA if less than 15 or greater than or equal to 100.	23
driver_race_raw	The original data value from which the driver’s standardized race is computed. Not in a standard format across states.	African American
driver_race	The standardized driver race. Possible values are White, Black, Hispanic, Asian, Other, and NA, with NA denoting values which are unknown. Asian refers to Asian, Pacific Islander, and Indian. Native Americans/American Indians are included in the "other" category. Anyone with Hispanic ethnicity is classified as Hispanic, regardless of their recorded race.	Black
violation_raw	The violation committed by the driver, in the language of the original data. Not in a standard format across states. Some stops have multiple violations.	Speeding (10–19 MPH Over Prima Facie Limit *)
violation	The violation committed by the driver, standardized into categories which are consistent across states.	Speeding
search_conducted	A TRUE/FALSE value indicating whether a search was performed.	TRUE
search_type_raw	The justification for the search, in the language of the original data. NA if no search was performed. Not in a standard format across states. Some states have multiple justifications for a search.	CONSENT SEARCH CONDUCTED
search_type	The normalized justification for the search. Where possible, this is standardized into categories which are consistent across states. For example, if something is clearly a consent search, search_type is referred to as “Consent”.	Consent
contraband_found	A TRUE/FALSE value indicating whether a search was performed and contraband was found. FALSE if no search was performed.	TRUE
stop_outcome	The outcome of the stop. Many states have idiosyncratic outcomes — for example, “CHP 215” in California — so this column is not standardized across states. “Citation” and “Warning” are the values which occur most commonly across states. If the stop has multiple outcomes, the most severe outcome is used. For example, if a stop resulted in a citation and a warning, stop_outcome would be “Citation”.	Citation
is_arrested	A TRUE/FALSE value indicating whether an arrest was made.	TRUE
