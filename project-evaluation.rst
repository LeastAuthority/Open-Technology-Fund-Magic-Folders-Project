
The evaluation will be whether it meets a set of functionality, usability,
and code-quality requirements.

Functionality and usability requirements are the reason for the project's
existence: to provide a safe and usable way to sync files.

The code-quality goals are necessary for sustainability, for adoption by the
community of Free and Open Source programmers, and they are also necessary
for security.

**Functionality**

The basic functionality is that the system can be used to share and
synchronize files and directories across multiple devices and users. It must
do so while preserving Tahoe-LAFS's security and fault-tolerance.

* *Data preservation*: the contents of a file will never be lost except when
  the users have explicitly requested deletion or overwrite. Even
  simultaneous edit of the same file by different users at the same time will
  result in the preservation of all of the edits performed by all users
  (although possibly not all under the same old filename).

* *Recoverability*: if a file is accidentally overwritten, then it is
   possible for the user to find and restore a previous version.

* *Explicit notification of conflict*: if a file is changed simultaneously on
   multiple devices, the users will see an explicit indication that there
   have been conflicting changes, instead of one change silently overwriting
   the other.

* *Least-Authority Access Control*: users can grant read-only access or
  read-write access to any subset of their files or any subtree of their
  directory structure.

* *Deduplication*: if the same file contents (the same sequence of bytes) is
  shared by multiple users or multiple devices, the ciphertext will be
  deduplicated so that only one copy of the file is stored on the servers,
  and only the first uploader has to upload the ciphertext.

* *Stabilization*: when the users have initiated changes to the system such
  as by saving new files or new versions of files into some Magic Folders,
  then after enough time has passed the system enters a quiescent state where
  no further changes will occur.

* *Forward Progress* and *Fairness*: if there is a continuous stream of new
  changes initiated such that the system never has a chance to quiesce, then
  at least such operations as it *can* complete it will complete.

  For example, if one file is repeatedly updated, as would be the case with a
  log file, then the system is required to continue making progress on
  synchronizing other files without waiting for that file to stop being
  updated. Likewise, if a file is repeatedly updating, the system is required
  to replicate *some* new version of the file instead of waiting to see what
  the "final" new version of the file will be.

**Usability**

In order to be usable, it will have to be *understandable*, *reliable*, and
*performant*.

*Understandable*

Can the user explain what happened? For example, if a user has a file named
“foo.doc”, which upon being edited simultaneously by two users, is copied
into two files, named “foo.doc (John's conflicted copy 2014-01-02)” and
“foo.doc (Bill's conflicted copy 2014-01-02)”, then they will be able to
understand what happened.

If instead, the file has silently been overwritten with one or the other
version, they may not realize what has happened and may have difficulty
explaining the result ¹, ², ³.

¹ Dropbox Documentation, “What's a conflicted copy?” (2014) <https://www.dropbox.com/help/36/en>

² Earle, D “Writer's Review—Dropbox vs Google Drive” (2012) <http://www.davidearle.com/2012/04/writers-review-dropbox-vs-google-drive.html>

³ Busch, J “Google Drive vs. Dropbox—A Challenger Appears!” (2012) <http://www.groovypost.com/reviews/dropbox-vs-google-drive/>

*Reliable*

Users avoid tools that cause problems, even if only occasionally. In order
for people to rely on Magic Folders, it must never accidentally lose the
user's files or their changes. Once a user requests an action, it must never
silently fail to complete the requested action.

For example, if the user indicates that a file should be shared by dragging
and dropping it into a Magic Folder, then the file will *eventually* be
shared (whenever the network connection to the servers is working), even if
the network connection to the servers was not working at the time the
drag-and-drop was first performed, *without* the user having to repeat the
drag-and-drop action.

*Performant*

Users prefer services that have low and steady latency. An important metric
will be the latency of propagation of updates. Latency will necessarily be a
sum of terms outside of our control — such as the performance of the network
— and terms inherent to our design. The *added* latency due to our design
(not caused by the performance of the network) will be considered acceptable
if it is less than 100 seconds, and excellent if it is less than 100
milliseconds.

*Quality Requirements*

* *Unit tests*: all code contributed to the Tahoe-LAFS project is required to
  have unit tests. To meet this standard, we develop the code and the unit
  tests together.

* *Documentation and Free and Open Source publication*: We will contribute
  all of the implementation source code to the Tahoe-LAFS project under the
  terms of its Free and Open Source Licences. This maximizes the
  opportunities for peer review, including security auditing by other
  contributors, for benefit to the public, and for other works to be built on
  top of this one.

  We'll also follow the Tahoe-LAFS project's quality standards, including
  developer-oriented and user-oriented documentation.

* *Statistics and logging*: the Magic Folder process exports operational
  statistics about performance and a record of exceptions or failures.

* *Failure handling*: either by retrying or by raising an informative error
  message (in addition to the logging mentioned above).

