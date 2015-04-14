
**Objective 1**

The deliverable for *Objective 1* is a document explaining the interface
between the sync client and the local filesystem, how the sync client will
register to watch subdirectories as they are created or moved into the
magic folders (including which APIs or libraries are to be used on Linux
and Windows platforms), and when the sync client will need to perform a
full rescan. This filesystem integration should be efficient, scalable to
large numbers of files and deep directory structure, and reliable, taking
into account changes while the sync client was not running.


**Objective 2**

*Objective 2* is to implement filesystem integration on Linux and Windows, as
defined by *Objective 1*. The deliverable for *Objective 2* is a fully tested
code-base (satisfying the requirements listed in the “Project Evaluation”
section) for those platforms.


**Objective 3**

The deliverable for *Objective 3* is the design document for how to do
remote-to-local synchronization. This includes how to efficiently determine
which remote files and directories have to be downloaded in order to bring
the current local filesystem into sync (minimizing unnecessary load), how
to distinguish between overwrites and conflicts, and how to overwrite the
stale local versions of those objects with the newly acquired objects
while avoiding the possibility of data loss.


**Objective 4**

*Objective 4* is to implement the remote-to-local sync algorithm as defined
by *Objective 3*. The deliverable for *Objective 4* is a fully tested
code-base implementing this and satisfying the requirements listed in the
“Project Evaluation” section.


**Objective 5**

*Objective 5* is to write the design document explaining how users can
conveniently and securely indicate which folders on some devices should be
magically linked to which folders on other devices.

As described in the “Narrative” section, this is a critical usability and
security issue for which there is no known perfect solution, but which will
hopefully be amenable to a "good enough" trade-off solution. The deliverable
for *Objective 5* is a document explaining this design and justifying its
trade-offs in terms of security, usability, and time-to-market.


**Objective 6**

*Objective 6* is to implement the folder-linking process as defined by
*Objective 5*. The deliverable for *Objective 6* is a fully tested
code-base implementing this and satisfying the requirements listed in the
“Project Evaluation” section.
