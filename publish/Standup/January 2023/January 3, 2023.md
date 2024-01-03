
- [x] Bryan 
- [x] Ben
- [x] Demetrius
- [x] Tony
- [x] Neil
- [x] Vitality

Yesterday
- Catch up on Slack/Email
- Review PR from last week
- Update Mac
- Admin task (forte)
Today
- Pull story off the board, most likely the only 2 active slot story
	- [jira](https://jira.atl.ring.com/browse/RP-63071)


## Unofficial TODO list
- [ ] Write rough draft of self review
- [ ] 1 Write rough draft for other
- [ ] 2 Write rough draft for other
- [ ] 3 Write rough draft for other
- [ ] 4 Write rough draft for other
- [x] Get back into Cloud Desktop
- [x] Recompile BL2 without latest branch
- [x] Determine where the SDK gets pulled in
	- [x] Look at git history
	- [x] Look at build script
		- **This is how it gets in on line # 109**
		- Note: the SBL2 is compiling fine.  The issue is compiling the MSFL against the new SBL2.  I noticed it was not doing this before Christmas break when I was printing the number of boot slots and the size of one of those slots.  Clearly I could see I was no operating on two slots, but the MSFL did not show this.  The reason is it was not being compile against the latest branch
			- **SOLUTION** Need to compile it against the latest branch.  Then I need to patch in any changes that I need to make to it as well, (if any that is)
	- [ ] Something else
 - [ ] Figure it out compile changes
	 - [ ] Where do the changes go
		 - Commit it
		 - Patch it
		 - Something else
- [ ] Review name change recommendations
- [ ] Get it to delete the partition with the new name
- [ ] Get it to flash the partition with the new name
- [ ] Update the self documentation with the new name
- [ ] Search confluence for where to update documentation
