<h1> Creating and Linking Group Policy Objects (GPO) in Active Directory</h1>

<h2>Prerequisites</h2>
•	Administrative access to a Windows Server with Active Directory Domain Services (AD DS) installed.<br />
•	Ensure you are logged in with a user account with the necessary permissions to create and link GPOs.

<h2>Step 1: Open Group Policy Management Console (GPMC)</h2>
<img src="https://imgur.com/a7GAPZl.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

You can access the Group Policy Management Console through the Server Manager Dashboard by clicking on “Tools” in the top right corner. Then click on Group Policy Management. 

<h2>Step 2: Create a new GPO</h2>
<img src="https://imgur.com/lx7DXaQ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

1.	In the Group Policy Management Console, navigate to the Forest and then to the Domain where you want to create the GPO. For example, Forest: yourdomain.com > Domains > yourdomain.com. In my case, the name of my domain name is “hsnetworks.local” 

<img src="https://imgur.com/CfetEdz.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

2.	Right-click the Group Policy Objects container and select New.

<img src="https://imgur.com/OeGGPmn.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

3.  In the New GPO dialog box, enter a name for the new GPO in the Name field. For example, Sample GPO.
4.	Optionally, you can enter a comment describing the purpose of the GPO in the Description field.
5.	Click OK to create the new GPO.

<h2>Step 3: Edit the new GPO</h2>
<img src="https://imgur.com/WSblCqf.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

1.	After creating the GPO, it will appear in the Group Policy Objects container. Right-click the newly created GPO (e.g., Sample GPO) and select Edit.

<img src="https://imgur.com/p78HsyV.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

2.	This will open the Group Policy Management Editor, where you can define the policies you want to enforce.

<h2>Step 4: Define Policies in the GPO</h2>
<img src="https://imgur.com/FPCfIlr.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

•	In the Group Policy Management Editor, expand User Configuration to reveal its subcategories.<br />
•	Expand Policies.<br />
•	Expand Administrative Templates.<br />
•	Click on the Start Menu and Taskbar. This will display a list of available policies related to the Start Menu and Taskbar in the right-hand pane.

<img src="https://imgur.com/xyqhwpV.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

•	Browse through the list of policies to find the one you want to configure. For this example, let's configure the "Remove Clock from the system notification area" policy.

<img src="https://imgur.com/EAYdvRf.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

•	Double-click on " Remove Clock from the system notification area " to open the policy settings.

<img src="https://imgur.com/m7PIWZL.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

•	In the policy settings window, you will see three options:<br />
      - NOT CONFIGURED: The policy setting is not defined.<br />
      - ENABLED: The policy setting is turned on.<br />
      - DISABLED: The policy setting is turned off.<br /> <br />
•	Select Enabled to remove the Run menu from the Start Menu.<br />
•	Optionally, you can add a comment in the Comment field to describe the purpose of enabling this policy.<br />
•	Click Apply, then OK to save the changes.

<img src="https://imgur.com/SPgbE6M.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

•	After configuring the policy, you can verify it by checking its state in the Group Policy Management Editor. The status of the policy should now show as Enabled.

•	After configuring your GPO in the Group Policy Management Editor, close the editor to return to the Group Policy Management Console (GPMC).<br />
•	In the Group Policy Management Console (GPMC), find the GPO you configured. This can be found under Forest > Domains > yourdomain.com > Group Policy Objects.<br />
•	Click on the GPO you configured (e.g., Sample GPO).

<h2>Generating a Report for the GPO Settings</h2>

<img src="https://imgur.com/4BZJWSk.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

1. Exit the Group Policy Management Editor<br />
  •	After configuring your GPO in the Group Policy Management Editor, close the editor to return to the Group Policy     Management Console (GPMC).<br />
  
2. Navigate to the GPO in GPMC<br />
  •	In the Group Policy Management Console (GPMC), find the GPO you configured. This can be found under Forest >         Domains > yourdomain.com > Group Policy Objects.<br />
  •	Click on the GPO you configured (e.g., Sample GPO).

3. Generate a Settings Report<br />
  •	With the GPO selected, in the right-hand pane, click on the Settings tab.<br />
  •	The Settings tab displays a report of all the configured settings in the GPO.

<img src="https://imgur.com/qS1HwZs.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

  •	In the Trusted Sites window, you can add the site "about.exe".<br />
  •	Type about:security_mmc.exe in the Add this website to the zone field.<br />
  •	Click Add to add it to the list of Trusted Sites.<br />
  •	Ensure that the required server verification (https:) for all sites in this zone checkbox is unchecked for this       entry, as "about:" URLs do not use HTTPS.

EXPLANATION:<br /><br />
•	Generating a Report: This step is useful for verifying the settings applied in a GPO. The report provides a clear, comprehensive view of all the configured policies, which is crucial for documentation and troubleshooting.<br />
•	Adding "about.exe" to Trusted Sites: This step ensures that certain management consoles (like GPMC) that may use this URL to display settings or security information are trusted by the browser, preventing any security prompts or issues that might block content.


<img src="https://imgur.com/z6SLLEH.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

Expand Policies > Administrative Templates. This section lists all the administrative templates and the specific policies that have been configured within the GPO.<br />
•  Look for the Start Menu and Taskbar category under Administrative Templates.<br />
•  Within the Start Menu and Taskbar category, locate the "Remove Clock from the system notification area" policy. There you will notice that it is set to “Enabled” <br />

Explanation of the Steps:<br /><br />
1.	Open GPMC: Access the Group Policy Management Console to manage and review GPOs.<br />
2.	Navigate to the GPO: Find the specific GPO you configured to see its settings.<br />
3.	View Configured Policies: The Settings tab provides a comprehensive report of all policies applied in the GPO, organized by categories.<br />
4.	Locate Specific Policy: Within the Administrative Templates section, you can see detailed configurations for each policy, including whether they are enabled or disabled.<br />

Additional Notes:<br /><br />
•	Policy Categories: Administrative Templates are a set of registry-based policy settings that appear in the Group Policy Management Editor. They are used to manage the user and computer settings for various Windows components.<br />
•	Policy Details: Viewing the policy details helps in understanding what specific settings have been applied and verifying that the intended policies are configured correctly.<br />

<h2>Link the GPO to an Organizational Unit (OU)</h2>

<img src="https://imgur.com/yEpXa6n.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

1.	Return to the Group Policy Management Console.<br />
2.	Navigate to the OU where you want to link the GPO. For example, Forest: yourdomain.com > Domains > yourdomain.com > OU_Name. In this case, the name of my Organizational Unit is “OU1”<br />
3.	Right-click the OU and select Link an Existing GPO.

<img src="https://imgur.com/HboKmGV.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

4.	All the GPOs that are enabled will show up in this Select GPO dialog box, including the Sample GPO you configured.<br />
5.	In the Select GPO dialog box, select the GPO you created (e.g., Sample GPO) from the list and click OK.<br />

<img src="https://imgur.com/fNM3z9T.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>

6.  The linked GPO should now appear in the Linked Group Policy Objects tab for the OU. <br />
7.  You can also view and manage the linked GPO from here, including setting link order and enabling/disabling the link.<br />

<h2>Step 7: Verify GPO Application</h2>

1.	To verify that the GPO is applied, you can use the Group Policy Results or Group Policy Modeling features in the Group Policy Management Console.<br />
2.	Right-click the domain or OU and select Group Policy Results Wizard to check the GPOs applied to a user or computer.<br />
3.	Follow the wizard to generate a report showing which policies are applied.<br />

<h2>Additional Considerations</h2>

1.  Security Filtering: You can use security filtering to apply the GPO to specific groups or users. This can be configured in the Scope tab of the GPO settings in the GPMC.<br />
2.  WMI Filtering: You can also use WMI filters to apply the GPO based on specific criteria such as OS version, hardware configuration, etc.<br />

