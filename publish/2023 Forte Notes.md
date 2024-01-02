
## January 2023

- MSP support where USB stick stopped mounting on and extended storage MSP
- SOP for backup/restore USB on extended storage MSP
	- [Ext MSP backup/restore](https://confluence.atl.ring.com/display/RS/MSP%3A+Restore+USB+storage+on+an+MSP+with+external+storage)
- AV1/AV2 from FR to MSP using new debutante package loader deploy
- Fixed AV2 MSP LED (loses control) issue after reboot
- MSP maintenance
- Integrated/rebased lib sedes library and worked with hub-core to expand
	- Made custom Kibo/CCG3 firmware to test/verify
	- Owned this change from John and had to determine what was relevant and should be committed
	- This required various rebases
	- Had to sync changes with hub-core
- available fault/failure messages made available to upper layers
- Panasonic Battery Qualification
	- Verified latest functionality of srec changes
	- Worked with Lab 126 (Camila)
	- [Jira - Panasonic Battery CFET failing qualification](https://jira.atl.ring.com/browse/RP-54797)
	- Note for myself this included 3D print battery holder, opened batteries up and shorted FET's, BQ studios, self made heat chamber, and precision power supply, updated srec in repos
	- Ultimately pushed decision based on ROI in the direction to decide that we did not require a second source qualification for Panasonic, since we already had X in inventory and only expected to run X more KMJ's
- Completed final check and verification of KMJ PCB 1.5
- HW clock write/read on shutdown/startup /w Ben
- Misc RFUT stories
- Prevent Kibo notification during update in production roll out

## February 2023

- Control Internal battery charge current via hub control
	- [Control Internal Charge Strategy](https://confluence.atl.ring.com/display/~dddodg@amazon.com/Decide+KMJ+Kibo+Charging+Strategy+When+Internal+Battery+is+Faulted)
	- Held meetings with Share holders to decide
	- [Rooted in this bug](https://jira.atl.ring.com/browse/RP-48923)
	- This required CCG3 firmware update
	- Pushed this to completion to determine if these upgrades were worth the ROI and risk associated with an update
	- Root cause was temporary multiple kibo/internal battery charge when coming out of fault states
	- IRL there were no issues (measured wattage in stack and documented), but based on budget scheme in beginning
	- Wrote various Jira's around this work
- CFET trigger reports 100% on trigger
	- [Bug](https://jira.atl.ring.com/browse/RP-54103)
	- modified KMJ internal battery to CFET trigger and test what is available in this state for options
- Recovered another extended storage MSP with USB stick failures
- KMJ Kernel installer updates
	- This required testing in tus-pod and verify no negative effects on AV1/AV2
	- Uses md5sum of partition install to prevent unnecessary mounting of partitions when they have already been updated

## March 2023

- Another RFUT bug
- MSP deletes
- More MSP deletes
- Another RFUT story
- Additional testing found that AV1 got blown away with latest kernel updates and it related to missing dosfstools binary (dependency)
- MSP maintenance

## April 2023

- Found fsck issues in AV1 relating to kernel update process
- Suppress warning for Kibo updates
	- This requires cache ing of kibo data for running in backup partition
- More RFUT bugs (delayed shutdown of ~3 minutes)
- PCB 1.5 additional checkout in MFG PMIC going into low power mode
	- SNVS power save state is not lowering power consumption as expected
	- Verified it was in the state and checked rails individually
	- Rails are as expected.  Updated the MFG SOP for PCB 1.5
- RSL updates that I owned and worked with RSL team on updates
	- RSL reverts, updates, reverts, etc
	- Anytime we insmod the drive it continously reset MCU
	- Did binary search through releases to find commit where it started
	- It started when they did a major rework of RSL driver
- Removed daily battery unlocks from KMJ

## May 2023
- Kibo story with accidentally masked bits
	- [Kibo faults testing wiki](https://confluence.atl.ring.com/display/~dddodg@amazon.com/Kibo+Recoverable+failures+are+not+reported+in+JSON+report)
- Kibo jira overtemperature not triggering fault code
	- sync'd with hub-core for these changes and others
## June 2023
- CFET failures report 100% jira - continued...
	- created temporary file to signal CFET failures to be loaded by pd-managment
	- This file is created by battery test which is done on boot up (or deleted if no CFET errors found)
	- Another story where Dean/Steve worked with me
- Now getting data back for what types of battery locks were in the field
	- 95 % were cell imbalance
- By this time of the year a regularly sync'd with Pat and sometimes Daniel on QA
- Removed non-functional code in pd-management for pass-through
	- sync'ing /w John on CFET/DFET test brought this about
- Story where KMJ does not power up (Daniel)
	- Battery never recieves shutdown
	- No PCB 1.5 in the field as of yet (or ever)
	- [jira](https://jira.atl.ring.com/browse/RP-46295)
- Story KMJ doesn't power up from (Niles)
	- Lot of work here to determine root cause to be ESD
	- [Story](https://confluence.atl.ring.com/display/~dddodg@amazon.com/Kibo+Recoverable+failures+are+not+reported+in+JSON+report)
	- [wiki](https://confluence.atl.ring.com/display/~dddodg@amazon.com/KMJ+doesn%27t+register+power+adapter+and+battery+dies)
## July 2023
- Created new story about failing to shipmode based off kernel virtual machine


# Brag/owned items of 2023
- PCB 1.5
- CCG3/Kibo firmware
- pd-management stack
- MSP
- MSP-extended storage
- Panasonic battery replacement
