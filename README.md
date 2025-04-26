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
