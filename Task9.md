[report.txt](https://github.com/user-attachments/files/19196521/report.txt)## Task 9: Analyze Your Image with Docker Scout
1. **Run Docker Scout Analysis:**  
   - Execute Docker Scout on your image to generate a detailed report of vulnerabilities and insights:
     ```bash
     docker scout cves <your-username>/sample-app:v1.0
     ```
   - Alternatively, if available, run:
     ```bash
     docker scout quickview <your-username>/sample-app:v1.0
     ```
     to get a summarized view of the image’s security posture.
   - **Optional:** Save the output to a file for further analysis:
     ```bash
     docker scout cves <your-username>/sample-app:v1.0 > scout_report.txt
     ```

2. **Review and Interpret the Report:**  
   - Carefully review the output and focus on:
     - **List of CVEs:** Identify vulnerabilities along with their severity ratings (e.g., Critical, High, Medium, Low).
     - **Affected Layers/Dependencies:** Determine which image layers or dependencies are responsible for the vulnerabilities.
     - **Suggested Remediations:** Note any recommended fixes or mitigation strategies provided by Docker Scout.
   - **Comparison Step:** If possible, compare this report with previous builds to assess improvements or regressions in your image's security posture.
   - If Docker Scout is not available in your environment, document that fact and consider using an alternative vulnerability scanner (e.g., Trivy, Clair) for a comparative analysis.

3. **Document Your Findings:**  
   - In your `solution.md`, provide a detailed summary of your analysis:
     - List the identified vulnerabilities along with their severity levels.
     - Specify which layers or dependencies contributed to these vulnerabilities.
     - Outline any actionable recommendations or remediation steps.
     - Reflect on how these insights might influence your image optimization or overall security strategy.
   - **Optional:** Include screenshots or attach the saved report file (`scout_report.txt`) as evidence of your analysis.

---
## Solution :-

### POC :- 

### 1.  docker scout cves <your-username>/sample-app:v1.0

![image](https://github.com/user-attachments/assets/a2629c94-9f1b-4d9f-b0f9-0058bfd96202)

![image](https://github.com/user-attachments/assets/cb09b9e1-6402-4d71-b8ae-2fa536debe52)

---

2. docker scout quickview <your-username>/sample-app:v1.0

![image](https://github.com/user-attachments/assets/6c3e0d03-079a-4b51-a06e-6a8fdecdfc07)

---
3.  docker scout cves <your-username>/sample-app:v1.0 > scout_report.txt

[Uploading report

## Overview

                    Γöé        Analyzed Image         
ΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓö╝ΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇΓöÇ
  Target            Γöé  deepak0202/app-mini:latest   
    digest          Γöé  1ee2b0cfcd4f                 
    platform        Γöé linux/amd64                   
    vulnerabilities Γöé    0C     3H     3M     1L    
    size            Γöé 26 MB                         
    packages        Γöé 62                            


## Packages and Vulnerabilities

   0C     2H     3M     1L  werkzeug 2.2.2
pkg:pypi/werkzeug@2.2.2

    x HIGH CVE-2024-34069 [Cross-Site Request Forgery (CSRF)]
      https://scout.docker.com/v/CVE-2024-34069?s=github&n=werkzeug&t=pypi&vr=%3C3.0.3
      Affected range : <3.0.3                                        
      Fixed version  : 3.0.3                                         
      CVSS Score     : 7.5                                           
      CVSS Vector    : CVSS:3.1/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:H/A:H  
    
    x HIGH CVE-2023-25577 [Uncontrolled Resource Consumption]
      https://scout.docker.com/v/CVE-2023-25577?s=github&n=werkzeug&t=pypi&vr=%3C2.2.3
      Affected range : <2.2.3                                        
      Fixed version  : 2.2.3                                         
      CVSS Score     : 7.5                                           
      CVSS Vector    : CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:H  
    
    x MEDIUM CVE-2024-49767 [Uncontrolled Resource Consumption]
      https://scout.docker.com/v/CVE-2024-49767?s=github&n=werkzeug&t=pypi&vr=%3C%3D3.0.5
      Affected range : <=3.0.5                                                          
      Fixed version  : 3.0.6                                                            
      CVSS Score     : 6.9                                                              
      CVSS Vector    : CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:N/VI:N/VA:L/SC:N/SI:N/SA:N  
    
    x MEDIUM CVE-2024-49766 [Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')]
      https://scout.docker.com/v/CVE-2024-49766?s=github&n=werkzeug&t=pypi&vr=%3C%3D3.0.5
      Affected range : <=3.0.5                                                          
      Fixed version  : 3.0.6                                                            
      CVSS Score     : 6.3                                                              
      CVSS Vector    : CVSS:4.0/AV:N/AC:H/AT:N/PR:N/UI:N/VC:L/VI:N/VA:N/SC:N/SI:N/SA:N  
    
    x MEDIUM CVE-2023-46136 [Uncontrolled Resource Consumption]
      https://scout.docker.com/v/CVE-2023-46136?s=github&n=werkzeug&t=pypi&vr=%3C2.3.8
      Affected range : <2.3.8                                        
      Fixed version  : 2.3.8                                         
      CVSS Score     : 5.7                                           
      CVSS Vector    : CVSS:3.1/AV:A/AC:L/PR:L/UI:N/S:U/C:N/I:N/A:H  
    
    x LOW CVE-2023-23934 [Improper Input Validation]
      https://scout.docker.com/v/CVE-2023-23934?s=github&n=werkzeug&t=pypi&vr=%3C2.2.3
      Affected range : <2.2.3                                        
      Fixed version  : 2.2.3                                         
      CVSS Score     : 2.6                                           
      CVSS Vector    : CVSS:3.1/AV:A/AC:H/PR:N/UI:R/S:U/C:N/I:L/A:N  
    

   0C     1H     0M     0L  flask 2.2.2
pkg:pypi/flask@2.2.2

    x HIGH CVE-2023-30861 [Use of Persistent Cookies Containing Sensitive Information]
      https://scout.docker.com/v/CVE-2023-30861?s=github&n=flask&t=pypi&vr=%3C2.2.5
      Affected range : <2.2.5                                                           
      Fixed version  : 2.2.5                                                            
      CVSS Score     : 8.7                                                              
      CVSS Vector    : CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:N/VA:N/SC:N/SI:N/SA:N  
    


7 vulnerabilities found in 2 packages
  LOW       1  
  MEDIUM    3  
  HIGH      3  
  CRITICAL  0  

.txt…]()

---
