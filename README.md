# possum_prefect_automation
Repository to enable POSSUM workflows automation with Prefect.
See more README in each folder.

* prefect_config -> Docker and OAuth2 Proxy configuration for POSSUM prefect v3 setup

We also contributed to the following repos. 
- https://github.com/CIRADA-Tools/POSSUMutils.git
- https://github.com/CIRADA-Tools/POSSUM_Polarimetry_Pipeline.git

The work is to:
- use POSSUM database to replace Google spreadsheets,
- setup REST API to serve/update the POSSUM database above,
- consume REST API from the POSSUM workflows in both CIRADA-Tools repos,
- added unit tests
