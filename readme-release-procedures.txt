 * Ensure staging is configured in settings.xml:

   <profile>
      <id>codehaus-release</id>
      <properties>
        <deploy.altRepository>mortbay.staging::default::scpexe://www.mortbay.org/home/ftp/pub/staging</deploy.altRepository>
      </properties>
    </profile>

* Update the glassfish cvs tag property in top level pom.xml.

* mvn clean release:prepare

* mvn release:perform

* Ensure next version is *.p1-SNAPSHOT

* Verify release on staging.

* To put live, change settings.xml:

   <profile>
      <id>codehaus-release</id>
      <properties>
        <deploy.altRepository>codehaus.org::default::dav:https://dav.codehaus.org/repository/jetty</deploy.altRepository>
      </properties>
    </profile>

  Then checkout the tag and run 'mvn -DupdateReleaseInfo=true deploy'
