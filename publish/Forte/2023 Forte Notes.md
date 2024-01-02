
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
- Niles hub ESD hardware absorbed two weeks to figure this out
- MSP maintenance with Crhis
	- This all ended up being networking issues and significant waste of resoureces from BSP
- Look at occasional dmesg lines caused by i2c device not being able to read registers (Dean)
	- [jira](https://jira.atl.ring.com/browse/RP-50387)
	- at this point it was mostly splunk sleuthing looking at temperature/cfet/communication errors
	- Did it persist over resets etc?
	- Found approximately 900 production units in this state
	- CFET/DFET not in prod at this point to cross reference with definitey
	- Brain stormed with Neil
	- Looked at decreasing battery voltage trends being connected to these messages
	- Pulled log on unit after unit and put trends found through greps into excel files to connect it with some other explanation for this behavior
- Story to cut down Kibo polling when
	- The majority of KMJ have no Kibo's and we optimized the polling pattern to reduce logs significantly for this case.  This reduced log footprint, and helps makes errors in the logs stand out easier
	- [jira](https://jira.atl.ring.com/browse/RP-49539)
	- Also important to keep code path similar for KMJ's with kibos since we do not want any regression issues or need to do heavy regression testing for this change
	- MSP clean up
## August 2023

- Summit
- Local builds for Blink
	- [jira](https://jira.atl.ring.com/browse/RP-61263)
	- [wiki](https://confluence.atl.ring.com/display/~dddodg@amazon.com/RP-61263%3A+%5BBilly%5D%5BSahara%5D+Improve+local+Yocto+build+process)
	- Clean up docker management
	- Rewrote buildme
	- Test all relevant build cases
	- Provided a demo to the team
	- Verified it worked on Cloud Desktop (Blink) and GB (Ring)
	- Dockers build on Mac not supported due to FS limiations
	- There were issues on the Blink side that they did not have there ask documented in the JIra.  They ended up making a Quip page, but took over a month to be ready
- More work with RSL updates/reverts testing etc.
- Started epic to clean up debug scripts, but it never got prioritized (for AES mainly)
	- I did hold a meeting for this to get some things figured out, but never got stakeholder push on this.
	- Started CCG3 Bug Bucket stories
		- Tried to solve quickly or close out if not worth while ROI
- 8/30/23 Start of the beging of oscillation (hokey pokey)
## September 2023

- Hokey Pokey
	- Worked with BSP team and found shoring i2c together caused similar errors
	- Started by documenting a pattern that matched all hubs and putting it in wiki
	- [wiki](https://confluence.atl.ring.com/pages/viewpage.action?pageId=1757302765)
	- Sampled all units called out by AES by pulling logs and verify they all fit the pattern
	- I was not able to reproduce until working with prod which required side-loading for testing
	- Then I was able to reproduce with the majority of the test cases
	- One culprit early on was the mutexing between pd-monitor and pd-controller since they reported different results during oscillation period
	- Added wires and set gpio's to verify that mutexing was always exclusive (it was)
	- Looked for a stop gap to prevent customer facing symptoms
	- Created CFET triggered batteries for testing by opening them up and shorting, running them up to temp, then opening them up and removing the short.  
	- I created 4 CFET batteries and side loaded 4 KMJ to create a test bed to allow more parallels testing
	- Found there was I2C communication outside of mutex due to IRQ services
	- Compared JSON through binary search to find variables that could be hard coded with results to prevent oscillations.  This method failed
	- Set up local repository to load pd-monitor updates during roll from 62-64 production version
	- We now run CFET triggered batteries in stage to catch a possible edge case in the future
	- Found a bug and fixed it with bias for action when I found an uneven open/close pair.  I wanted to get it into next release cut which occurred in a few days.  If I was right then it would give a solution 8 weeks sooner in prod.  If wrong then no harm no foul. (8/29/23)

## October 2023

- Release 66 cut on Oct 4 to Stage.  Due to bias for action this has the oscillation fix
- CCG3 bug bucket resolve hub shutdown due to 99 being returned 
- Created SOP utilizing backup/restore for AES to replace CFET/DFET triggered hubs
- Attempted to pull TI serial numbers out of fielded KMJ battery packs (no value)
- Got CFET triggered batteries into stage and continuously monitor them
- Worked with Ben/Guhan to get a list of CFET/DFET triggered batteries that needed replacement in prod.  Also statistically, compare whether latest SREC decreases CFET/DFET occurences as expected. (nope)
- Looked @ Pat's 1% fail story
- Looked @ story around Balog's hubs with kibos attached shutdown.  
- (10/12/23) Blink finishes quip for local build so this work is unblocked
- Balog's unit reevaluted and working theory documented
	- [wiki](https://confluence.atl.ring.com/pages/viewpage.action?pageId=1817862669)
	- story closed with these results plus not enough impact
- Fixed eero-reset script that returns outputs integer conversion error
- Switched back to local build script for Blink on Cloud Desktop
- Spot checked for oscillation in release 66 (10/19/23)
- track Release 66 swing to look for oscillations as the hubs took the update (none)
	- Created a splunk search and rechecked every few days
- Review Blink quip with the team to narrow down the ask
- Ran 4 simultaneous Cloud Desktop for testing Blink local builds

## November 2023

- Completed Blink local build demo for the team
- 
## Brag/owned items of 2023

- PCB 1.5
- CCG3/Kibo firmware
- pd-management stack
- MSP
- MSP-extended storage
- Panasonic battery replacement
- Owned communication with AES and attend Chris bi-weekly meeting to allow a conduit to get help with common customer problems that are impactful enough to consider
- Local Buildme script for Blink for Billy/Sahara/rfut
- Owned RSL halo updates/reverts sanity testing with Pat
- CCG3/CCG4 Bug Bucket (also general KMJ stuff as well)

