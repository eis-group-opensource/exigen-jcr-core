The basic build procedure is like this:
 
1) Change the "patch level" in exigen-jcr-core/pom.xml <version> (to next -eN number; -e8 I for example) and built patch artifact ("mvn install").
1.1) Update "patch level" in exigen-jcr-core/original.pom.xml
2) Verify it worked, next also build sources artifact (see exigen-jcr-core-sources/ howto.txt, basically  do 'mvn install', then edit the zip-sources.cmd and run)
3) Send the verified patch artifacts to CI team to put on Nexus repository as new version (7.1.1.007-e8).
Send the original.pom.xml along with patch artifacts! (Do not send pom.xml that was used for building this patch.)

3.1) you are almost done.

4) In main eispom (projects root pom.xml), change <com.exigen.jcr.core.version> from old patch version (7.1.1.007-e7) to new patch level.
Now when project builds, it will get the patched artifact (say, exigen-jcr-core-7.1.1.007-e8.jar )

4.1) You may need to release "staging eispom".

***

When patching something new, rembember first put in orginal *unmodified* java file and commit.
Then edit with your changes, do new commit. So that in this commit you can see the modification that was done for patch.
