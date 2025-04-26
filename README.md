TC_16.feature
Feature:Site Name Update
  @ays_27
  Scenario : User want to update Site Name
    Given user lanuches FuzeapplicationUAT for "TC_1002"
    Then user verify the SPM application
    When user user click on the support module

-------------
Initialbuildsmallcell.java
@When("{actor} user click on the support module")
public void userClickOnTheSupportModule(Actor actor) throws IOException{
    actor.attemptsTo(Wait.timeInSeconds(3));
    actor.attemptsTo(Click.on(IBpage.SUPPORT_TAB));
    actor.attemptsTo(Wait.timeInSeconds(3));
    actor.attemptsTo(Click.on(IBpage.SUPPORT_TAB));
    actor.attemptsTo(Wait.timeInSeconds(3));
    actor.attemptsTo(Click.on(IBpage.SITEUPDATEBTN));

        Click.on(IBpage.SITE_ID_SEARCH);
                actor.attemptsTo(IBsmallcell.EnterSiteId());

        //WaitUntil.the(visibilityOfElementLocated(IBpage.SITE_NAME_SEARCH)),
        Click.on(IBpage.SITE_NAME_SEARCH);
        actor.attemptsTo(IBsmallcell.EnterSiteName());
      actor.attemptsTo(Wait.timeInSeconds(3));

        Click.on(IBpage.SITE_OPTION_CLICK);
        //WaitUntil.the(visibilityOfElementLocated(IBpage.NEW_SITE_NAME)),
        Click.on(IBpage.NEW_SITE_NAME);
        actor.attemptsTo(IBsmallcell.EnterNewSiteName());

        actor.attemptsTo(Click.on(IBpage.NEW_STATUS_CLICK));
    actor.attemptsTo(Click.on(IBpage.NEW_STATUS_DROPDOWN));

    actor.attemptsTo(Click.on(IBpage.NEW_TYPE_CLICK));
    actor.attemptsTo(Click.on(IBpage.NEW_TYPE_DROPDOWN));

    actor.attemptsTo(Click.on(IBpage.NEW_SUB_TYPE_CLICK));
    actor.attemptsTo(Click.on(IBpage.NEW_SUB_TYPE_DROPDOWN));

    actor.attemptsTo(Click.on(IBpage.APPLY_CHANGES));
        actor.attemptsTo(Wait.timeInSeconds(3));
    }

    -----------------------------------

    IBsmallcell.java

public static Performable EnterSiteId() {
    return Task.where(
            Enter.theValue("617498202").into(IBpage.SITE_ID_SEARCH)
    );
}

public static Performable EnterSiteName() {
    return Task.where(
            Enter.theValue("STUART N098").into(IBpage.SITE_NAME_SEARCH)
    );
}
public static Performable EnterNewSiteName() {
    return Task.where(
            Enter.theValue("WST_WHP_N048").into(IBpage.NEW_SITE_NAME)
    );
}

---------------------------------------
IBpage.java
 public final static By SITEUPDATEBTN =By.xpath("//button[@class='support-main-btn support_operation site_name_status_operation' and text()='Site Updates']");
    public final static By SITE_NAME_SEARCH= By.xpath("//input[@placeholder='Search Site Here']");
    public final static By SITE_ID_SEARCH =By.xpath("//div[@class='col-sm-4']/input[@class='form-control selected_site_id']");
    public final static By NEW_SITE_NAME=By.xpath("//input[@class='form-control new_site_name']");
    public final static By NEW_STATUS_CLICK=By.xpath("//select[@class='form-control new_site_status']");
    public final static By NEW_STATUS_DROPDOWN=By.xpath("//select[contains(@class, 'form-control') and contains(@class, 'site')]/option[@value='SarfSite']");
    public final static By NEW_TYPE_CLICK=By.xpath("//select[@class='form-control new_site_type']");
    public final static By NEW_TYPE_DROPDOWN=By.xpath("//select[@class='form-control new_site_type']/option[@value='MACRO']");
    public final static By NEW_SUB_TYPE_CLICK=By.xpath("//select[@class='form-control new_site_sub_type']");
    public final static By NEW_SUB_TYPE_DROPDOWN=By.xpath("//select[@class='form-control new_site_sub_type']/option[text()='CRAN']");
    public final static By APPLY_CHANGES=By.xpath("//button[@class='btn btn-sm btn-primary update_site_details_btn']");
public final static By SITE_OPTION_CLICK=By.xpath("//span[text()='617498202']");


-------------------------------------------------------
pom.xml

<?xml version="1.0"
encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>net.serenitybdd.starter</groupId>
    <artifactId>serenity-fuze-e2e</artifactId>
    <version>1.0.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>Sample Serenity BDD project using Cucumber</name>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <serenity.version>4.1.12</serenity.version>
        <junit-vintage-engine.version>5.10.2</junit-vintage-engine.version>
        <junit-platform-suite.version>1.10.2</junit-platform-suite.version>
        <cucumber-junit-platform-engine.version>7.16.1</cucumber-junit-platform-engine.version>
        <encoding>UTF-8</encoding>
        <tags></tags>
        <webdriver.base.url></webdriver.base.url>
    </properties>
    <pluginRepositories>
        <pluginRepository>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <id>central</id>
            <name>plugins-release</name>
            <url>https://oneartifactoryci.verizon.com/artifactory/plugins-release</url>
        </pluginRepository>
    </pluginRepositories>
    <repositories>
        <repository>
            <id>central</id>
            <name>libs-release</name>
            <url>https://oneartifactoryci.verizon.com/artifactory/libs-release</url>
        </repository>
        <repository>
            <snapshots/>
            <id>snapshots</id>
            <name>libs-snapshot</name>
            <url>https://oneartifactoryci.verizon.com/artifactory/libs-snapshot</url>
        </repository>
    </repositories>
    <dependencies>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-core</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-cucumber</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-screenplay-rest</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-screenplay</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-screenplay-webdriver</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-ensure</artifactId>
            <version>${serenity.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.junit.platform</groupId>
            <artifactId>junit-platform-launcher</artifactId>
            <version>${junit-platform-suite.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>io.cucumber</groupId>
            <artifactId>cucumber-junit-platform-engine</artifactId>
            <version>${cucumber-junit-platform-engine.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.junit.platform</groupId>
            <artifactId>junit-platform-suite</artifactId>
            <version>${junit-platform-suite.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>${junit-vintage-engine.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.junit.vintage</groupId>
            <artifactId>junit-vintage-engine</artifactId>
            <version>${junit-vintage-engine.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
            <version>1.2.11</version>
        </dependency>
        <dependency>
            <groupId>org.assertj</groupId>
            <artifactId>assertj-core</artifactId>
            <version>3.23.1</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>commons-httpclient</groupId>
            <artifactId>commons-httpclient</artifactId>
            <version>3.1</version>
        </dependency>
        <dependency>
            <groupId>org.json</groupId>
            <artifactId>json</artifactId>
            <version>20190722</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi</artifactId>
            <version>5.2.3</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-ooxml</artifactId>
            <version>5.2.3</version>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>net.serenity-bdd.maven.plugins</groupId>
                <artifactId>serenity-maven-plugin</artifactId>
                <version>${serenity.version}</version>
                <configuration>
                    <tags>${tags}</tags>
                    <reports>single-page-html</reports>
                </configuration>
                <dependencies>
                    <dependency>
                        <groupId>net.serenity-bdd</groupId>
                        <artifactId>serenity-single-page-report</artifactId>
                        <version>${serenity.version}</version>
                    </dependency>
                </dependencies>
                <executions>
                    <execution>
                        <id>serenity-reports</id>
                        <phase>post-integration-test</phase>
                        <goals>
                            <goal>aggregate</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.1.2</version>
                <configuration>
                    <skip>true</skip>
                </configuration>
            </plugin>
            <plugin>
                <artifactId>maven-failsafe-plugin</artifactId>
                <version>3.1.2</version>
                <configuration>
                    <includes>
                        <include>**/*Test.java</include>
                        <include>**/Test*.java</include>
                        <include>**/*TestSuite.java</include>
                        <include>**/When*.java</include>
                    </includes>
                    <systemPropertyVariables>
                        <webdriver.base.url>${webdriver.base.url}</webdriver.base.url>
                    </systemPropertyVariables>
                    <parallel>classes</parallel>
                    <parallel>methods</parallel>
                    <useUnlimitedThreads>true</useUnlimitedThreads>
                </configuration>
                <executions>
                    <execution>
                        <goals>
                            <goal>integration-test</goal>
                            <goal>verify</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.10.1</version>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>


-----------------------------------------------------------

ERROR:

C:\Users\lpxxar\.jdks\ms-21.0.6\bin\java.exe -Dmaven.multiModuleProjectDirectory=C:\Users\lpxxar\git\fuze_e2e_automation -Djansi.passthrough=true "-Dmaven.home=C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\plugins\maven\lib\maven3" "-Dclassworlds.conf=C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\plugins\maven\lib\maven3\bin\m2.conf" "-Dmaven.ext.class.path=C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\plugins\maven\lib\maven-event-listener.jar" "-javaagent:C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\lib\idea_rt.jar=58236:C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\bin" -Dfile.encoding=UTF-8 -Dsun.stdout.encoding=UTF-8 -Dsun.stderr.encoding=UTF-8 -classpath "C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\plugins\maven\lib\maven3\boot\plexus-classworlds-2.8.0.jar;C:\Program Files (x86)\JetBrains\IntelliJ IDEA Community Edition 2024.3.3\plugins\maven\lib\maven3\boot\plexus-classworlds.license" org.codehaus.classworlds.Launcher -Didea.version=2024.3.3 clean verify -Dcucumber.filter.tags=@AYS_27
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< net.serenitybdd.starter:serenity-fuze-e2e >--------------
[INFO] Building Sample Serenity BDD project using Cucumber 1.0.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.2.0:clean (default-clean) @ serenity-fuze-e2e ---
[INFO] Deleting C:\Users\lpxxar\git\fuze_e2e_automation\target
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ serenity-fuze-e2e ---
[INFO] skip non existing resourceDirectory C:\Users\lpxxar\git\fuze_e2e_automation\src\main\resources
[INFO] 
[INFO] --- compiler:3.10.1:compile (default-compile) @ serenity-fuze-e2e ---
[INFO] No sources to compile
[INFO] 
[INFO] --- resources:3.3.1:testResources (default-testResources) @ serenity-fuze-e2e ---
[INFO] Copying 59 resources from src\test\resources to target\test-classes
[INFO] 
[INFO] --- compiler:3.10.1:testCompile (default-testCompile) @ serenity-fuze-e2e ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 44 source files to C:\Users\lpxxar\git\fuze_e2e_automation\target\test-classes
[INFO] /C:/Users/lpxxar/git/fuze_e2e_automation/src/test/java/starter/stepdefinitions/InitialBuildsmallcell.java: Some input files use or override a deprecated API.
[INFO] /C:/Users/lpxxar/git/fuze_e2e_automation/src/test/java/starter/stepdefinitions/InitialBuildsmallcell.java: Recompile with -Xlint:deprecation for details.
[INFO] /C:/Users/lpxxar/git/fuze_e2e_automation/src/test/java/starter/teststeps/Sites.java: Some input files use unchecked or unsafe operations.
[INFO] /C:/Users/lpxxar/git/fuze_e2e_automation/src/test/java/starter/teststeps/Sites.java: Recompile with -Xlint:unchecked for details.
[INFO] 
[INFO] --- surefire:3.1.2:test (default-test) @ serenity-fuze-e2e ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- jar:3.4.1:jar (default-jar) @ serenity-fuze-e2e ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: C:\Users\lpxxar\git\fuze_e2e_automation\target\serenity-fuze-e2e-1.0.0-SNAPSHOT.jar
[INFO] 
[INFO] --- failsafe:3.1.2:integration-test (default) @ serenity-fuze-e2e ---
[INFO] Using auto detected provider org.apache.maven.surefire.junitplatform.JUnitPlatformProvider
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[ERROR] TestEngine with ID 'junit-platform-suite' failed to discover tests
[INFO] 
[INFO] Results:
[INFO] 
[INFO] Tests run: 0, Failures: 0, Errors: 0, Skipped: 0
[INFO] 
[INFO] 
[INFO] --- serenity:4.1.12:aggregate (serenity-reports) @ serenity-fuze-e2e ---
[INFO] GENERATING REPORTS FOR: C:\Users\lpxxar\git\fuze_e2e_automation
[INFO] GENERATING REPORTS USING 8 THREADS
[INFO] GENERATING SUMMARY REPORTS...
[INFO] GENERATING REQUIREMENTS REPORTS...
[INFO] GENERATING RESULT REPORTS...
[INFO] GENERATING ERROR REPORTS...
[INFO] Test results for 0 tests generated in 10 secs in directory: file:/C:/Users/lpxxar/git/fuze_e2e_automation/target/site/serenity/
[INFO]   - Single Page HTML Summary: file:///C:/Users/lpxxar/git/fuze_e2e_automation/target/site/serenity/serenity-summary.html
[INFO] 
[INFO] --- failsafe:3.1.2:verify (default) @ serenity-fuze-e2e ---
[WARNING]  Parameter 'encoding' (user property 'encoding') is deprecated: since of 2.20.1
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  29.821 s
[INFO] Finished at: 2025-04-26T23:23:15+05:30
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-failsafe-plugin:3.1.2:verify (default) on project serenity-fuze-e2e: 
[ERROR] 
[ERROR] Please refer to C:\Users\lpxxar\git\fuze_e2e_automation\target\failsafe-reports for the individual test results.
[ERROR] Please refer to dump files (if any exist) [date].dump, [date]-jvmRun[N].dump and [date].dumpstream.
[ERROR] There was an error in the forked process
[ERROR] TestEngine with ID 'junit-platform-suite' failed to discover tests
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.fork(ForkStarter.java:628)
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.run(ForkStarter.java:285)
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.run(ForkStarter.java:250)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.executeProvider(AbstractSurefireMojo.java:1203)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.executeAfterPreconditionsChecked(AbstractSurefireMojo.java:1055)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.execute(AbstractSurefireMojo.java:871)
[ERROR] 	at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:126)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2(MojoExecutor.java:328)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute(MojoExecutor.java:316)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:212)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:174)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.access$000(MojoExecutor.java:75)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor$1.run(MojoExecutor.java:162)
[ERROR] 	at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute(DefaultMojosExecutionStrategy.java:39)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:159)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:105)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:73)
[ERROR] 	at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:53)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleStarter.execute(LifecycleStarter.java:118)
[ERROR] 	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:261)
[ERROR] 	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:173)
[ERROR] 	at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:101)
[ERROR] 	at org.apache.maven.cli.MavenCli.execute(MavenCli.java:906)
[ERROR] 	at org.apache.maven.cli.MavenCli.doMain(MavenCli.java:283)
[ERROR] 	at org.apache.maven.cli.MavenCli.main(MavenCli.java:206)
[ERROR] 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
[ERROR] 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:255)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:201)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:361)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:314)
[ERROR] 	at org.codehaus.classworlds.Launcher.main(Launcher.java:41)
[ERROR] 
[ERROR] org.apache.maven.surefire.booter.SurefireBooterForkException: There was an error in the forked process
[ERROR] TestEngine with ID 'junit-platform-suite' failed to discover tests
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.fork(ForkStarter.java:628)
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.run(ForkStarter.java:285)
[ERROR] 	at org.apache.maven.plugin.surefire.booterclient.ForkStarter.run(ForkStarter.java:250)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.executeProvider(AbstractSurefireMojo.java:1203)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.executeAfterPreconditionsChecked(AbstractSurefireMojo.java:1055)
[ERROR] 	at org.apache.maven.plugin.surefire.AbstractSurefireMojo.execute(AbstractSurefireMojo.java:871)
[ERROR] 	at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:126)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2(MojoExecutor.java:328)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute(MojoExecutor.java:316)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:212)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:174)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.access$000(MojoExecutor.java:75)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor$1.run(MojoExecutor.java:162)
[ERROR] 	at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute(DefaultMojosExecutionStrategy.java:39)
[ERROR] 	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:159)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:105)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:73)
[ERROR] 	at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:53)
[ERROR] 	at org.apache.maven.lifecycle.internal.LifecycleStarter.execute(LifecycleStarter.java:118)
[ERROR] 	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:261)
[ERROR] 	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:173)
[ERROR] 	at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:101)
[ERROR] 	at org.apache.maven.cli.MavenCli.execute(MavenCli.java:906)
[ERROR] 	at org.apache.maven.cli.MavenCli.doMain(MavenCli.java:283)
[ERROR] 	at org.apache.maven.cli.MavenCli.main(MavenCli.java:206)
[ERROR] 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
[ERROR] 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:255)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:201)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:361)
[ERROR] 	at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:314)
[ERROR] 	at org.codehaus.classworlds.Launcher.main(Launcher.java:41)
[ERROR] 
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException

Process finished with exit code 1

