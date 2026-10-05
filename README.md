# SIEM--Authentication-Event-Correlation
Authentication Event Correlation

**Authentication Event Correlation**

**Objective**

Correlate failed and successful Windows authentication events to understand the authentication sequence observed by Wazuh.

Observed Events

Event	                          Event ID	          Account	                            Logon Type	                                Source
Failed authentication	             4625	             Nihan	                               2                                	     127.0.0.1
Successful authentication	         4624	             Nihan	                               2                                     	 127.0.0.1

Analysis

The Wazuh dashboard showed multiple failed authentication events followed by a successful interactive logon for the same local Windows account.

The failed events represented incorrect-password attempts generated during controlled testing. A subsequent successful Event ID 4624 confirmed that the account was able to authenticate successfully.

Because the activity was intentionally generated on the test Windows endpoint, the observed sequence was assessed as benign laboratory activity.

SOC Learning

Authentication events should be analyzed as a sequence rather than individually. Correlating failed and successful logons provides additional context and can help an analyst determine whether an authentication event requires further investigation.

Observed sequence:

4625 Failed → 4625 Failed → 4625 Failed → 4624 Successful
