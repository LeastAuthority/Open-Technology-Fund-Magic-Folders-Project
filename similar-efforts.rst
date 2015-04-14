
1. Martus (<https://www.martus.org/>) is a data management system.
   * Like Tahoe-LAFS, Martus does end-to-end encryption of the files.
   * Martus is targeted specifically at the human rights and NGO sector, and has features and UI specifically for creating organizations, documenting the provenance of bulletins, searching bulletins, etc.; Tahoe-LAFS is a generic utility with a minimal "programmer-oriented" user interface.
   * Martus does not currently have simple "Dropbox-like" synchronization behavior.
   * Martus is written in Java, Tahoe-LAFS is written in Python.
   * Tahoe-LAFS seems to have a wider community of contributors right now.
   * Benetech (the maintainers of Martus) and LeastAuthority would be interested in exploring whether Martus could use Tahoe-LAFS as an internal component.

2. git-annex assistant (<http://git-annex.branchable.com/assistant/>) is an open-source revision-controlled file sharing system.
   * git-annex assistant is not currently as easy to use as we intend for Magic Folder to be.
   * git-annex assistant does not have the security properties of Tahoe-LAFS.
   * git-annex assistant has the option of leveraging the security properties of Tahoe-LAFS by running on top of it; We've worked with the author of git-annex assistant to make that possible, and intend to continue to do so.
   
3. The Freenet (<https://freenetproject.org/>) project is a widely distributed Free and Open Source content sharing and publication system.
   * Freenet has a built-in anonymizing protocol, Tahoe-LAFS is more compartmentalized, depending on sister projects like Tor and I2P for anonymity properties.
   * Freenet is implemented in Java, Tahoe-LAFS is implemented in Python.
   * Freenet adopted a browser-based interface several years after Tahoe-LAFS.
   * Freenet and Tahoe-LAFS have evolved in similar but non-identical directions since their respective inceptions (<https://tahoe-lafs.org/pipermail/tahoe-dev/2011-July/006560.html>).

4. BT Sync (<http://www.bittorrent.com/sync>) is a peer-to-peer file-sharing app, from the inventors of BitTorrent..
   * BT Sync is closed-source software.
   * BT Sync replicates files directly from one device to the next, such that the cleartext of the file is available to each device that handles a replica of the file. This is appropriate for a use case in which all of the involved devices are authorized to read and edit the file contents, and the owners of all of the involved devices are *interested* in the file and willing to host it, but it is unsuitable for a "private hosted storage" model, as in Tahoe-LAFS, which encrypts each file so that the ciphertext of the file can be hosted by a service which is unable to view, and interested in, the file's contents.
