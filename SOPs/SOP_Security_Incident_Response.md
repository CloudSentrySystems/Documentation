# Security Incident Response Standard Operating Procedure (SOP)

## Purpose

Purpose of this SOP is to outline the process of identifying, classifying, responding to, investigating, recovering from, and reviewing security incidents in a cloud computing infrastructure.

## Scope

To establish a standardized and reliable method for performing regular security incident response procedures in [Your Organization Name]'s cloud computing infrastructure.

## Responsibilities

* **Security Team**: Responsible for identifying, classifying, and responding to security incidents.
* **IT Team**: Responsible for investigating and recovering from security incidents.
* **Management**: Responsible for reviewing security incidents and implementing action items.

## Prerequisites

**IAM**:
  * Ensure that the root account follows IAM best practices.
  * Implement proper IAM for all team members following AWS best practices.

**Server Hardening and Data Protection**:
  * Ensure that the Windows Server DC is CIS-compliant, hosted on a private subnet of a VPC, and is only accessible via VPN tunneling.
  * Data on the Windows Server DC must be encrypted both at rest and in transit.
  * Deploy Sysmon on the Windows Server DC to generate security-relevant system logs.
  * Ensure the Linux server instance containing PII and PCI data is CIS-compliant.
  * Data on the Linux server must be encrypted both at rest and in transit.

**SIEM / Log Aggregation System**:
  * Ensure that Splunk, CloudWatch, and Elastic Stack are properly configured to ingest event logs in real-time from key assets, including EC2 instances.
  * Monitor for specific attack TTPs, especially those that incorporate unfamiliar Python scripts. Any detected attack should trigger an event that gets ingested by the SIEM solution.

**Cloud Monitoring**:
  * Ensure that VPC Flow Logs are capturing traffic for the client to demonstrate how attack TTPs would be detected in the AWS Cloud.
  * Implement an AWS Lambda function that triggers a relevant response to a detected threat.
  * Monitor for threat activity in the AWS environment, especially failed SSH attempts on instances.

## Procedure

**Incident Identification**:
   * Monitor for automated alerts from the SIEM system, especially Splunk, CloudWatch, and Elastic Stack.
   * Review manual reports from users or IT staff.
   * Monitor for specific attack TTPs, especially those that incorporate unfamiliar Python scripts.

**Incident Classification**:
   * Classify the incident based on its severity and impact.
   * Determine the appropriate response based on the classification and type of attack.

**Incident Response**:
   * Initiate the response based on the classification of the incident.
   * If the attack incorporates unfamiliar Python scripts, ensure that the event is ingested by the SIEM solution.
   * Trigger the AWS Lambda function for a relevant response to a detected threat.

**Incident Investigation**:
   * Conduct an investigation to determine the cause of the incident.
   * Identify potential improvements to prevent similar incidents in the future.

**Incident Recovery**:
   * Take recovery actions to restore any affected services or data.

**Incident Review**:
   * Conduct a review to learn from the incident and improve future responses.
   * Implement action items to improve the security posture of the organization.

## Incident Response Diagram

![NIST Protocol Tailored for Cloud Infrastructure](https://imgr.whimsical.com/thumbnails/HQPQbYJU3u15DDRP8jRahV/JVw34jkvkyV816vfLPXZ77)

## Testing Procedures

**Test IAM Policies**:
   * Ensure all IAM policies are correctly configured and follow best practices.
   * **Expected Outcome**: All IAM policies are correctly configured and follow best practices.

**Test Server Hardening and Data Protection**:
   * Ensure the Windows Server DC is CIS-compliant and data is encrypted at rest and in transit.
   * Ensure the Linux server instance containing PII and PCI data is CIS-compliant and data is encrypted at rest and in transit.
   * **Expected Outcome**: The Windows Server DC and Linux server are hardened, and data is encrypted.

**Test SIEM / Log Aggregation System**:
   * Ensure that the SIEM system is properly configured to ingest event logs in real-time from key assets.
   * Monitor for specific attack TTPs and verify the SIEM's capability to detect and alert on them.
   * **Expected Outcome**: The SIEM system is fully functional.

**Test Cloud Monitoring**:
   * Verify that VPC Flow Logs are capturing traffic to detect attack TTPs.
   * Test the AWS Lambda function's capability to trigger relevant responses to detected threats.
   * Monitor for threat activity in the AWS environment, especially failed SSH attempts on instances.
   * **Expected Outcome**: The cloud monitoring setup is fully functional.




## References
- https://www.netwrix.com/cloud_security_policy.html
- https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf

## Definitions

- **Security Incident**: Any violation of policy, law, or unacceptable act that involves information assets, such as computers, networks.
- **SIEM**: Security Information and Event Management, a system that provides real-time analysis of security alerts generated by applications and network hardware.

## Revision History

- 08/07/2023 Dustin Haggett

