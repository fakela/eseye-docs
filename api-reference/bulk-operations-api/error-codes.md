# Error codes

The response file reports `completedStatus` as `Success` or `Failed` for each SIM. For failed SIMs, the file returns one of these error codes:

| errorId | errorName                                          | errorDescription                                                                       |
| ------- | -------------------------------------------------- | -------------------------------------------------------------------------------------- |
| 6001    | forbidden                                          | Forbidden                                                                              |
| 6002    | not\_found                                         | {resource} not found                                                                   |
| 6003    | method\_not\_allowed                               | Method not allowed                                                                     |
| 6004    | internal\_server\_error                            | Internal server error                                                                  |
| 6005    | not\_implemented                                   | Endpoint not yet implemented                                                           |
| 6006    | bad\_request                                       | Bad request                                                                            |
| 6007    | invalid\_status\_error                             | Status transition not allowed                                                          |
| 6008    | invalid\_user\_error                               | No session could be found for user                                                     |
| 6009    | invalid\_user\_error                               | No access available for this client                                                    |
| 6010    | invalid\_request\_error                            | MFA must be enabled                                                                    |
| 6011    | invalid\_request\_error                            | No fields requested from DB                                                            |
| 6012    | invalid\_data\_error                               | More than one record found in DB                                                       |
| 6013    | invalid\_data\_error                               | Invalid value for FK field                                                             |
| 6014    | invalid\_request\_error                            | Invalid value for given field                                                          |
| 6015    | invalid\_request\_error                            | No fields specified for change master                                                  |
| 6016    | invalid\_request\_error                            | Error from stored procedure                                                            |
| 6017    | invalid\_request\_error                            | No changes requested                                                                   |
| 6018    | invalid\_data\_error                               | Object deletion issue                                                                  |
| 6019    | invalid\_data\_error                               | Object deletion issue, multiple matches                                                |
| 6020    | invalid\_data\_error                               | Missing "{resource\_name}" value to perform authorization                              |
| 6021    | invalid\_request\_error                            | Can only authorize one resource                                                        |
| 6022    | invalid\_request\_error                            | Resource cannot be filtered by portfolio                                               |
| 6023    | invalid\_request\_error                            | {resource} not active                                                                  |
| 6024    | invalid\_request\_error                            | User does not have required permissions                                                |
| 6025    | invalid\_request\_error                            | User does not have required sphere                                                     |
| 6026    | invalid\_request\_error                            | Portfolio is not in sphere                                                             |
| 6027    | invalid\_request\_error                            | Portal is not in sphere                                                                |
| 6028    | invalid\_request\_error                            | User must have secure ID                                                               |
| 6029    | invalid\_request\_error                            | Vault update restricted to single item                                                 |
| 6030    | invalid\_request\_error                            | Unable to retrieve created vault data                                                  |
| 6031    | invalid\_request\_error                            | Only one context ID allowed                                                            |
| 6032    | invalid\_request\_error                            | contextPortfolioId not allowed                                                         |
| 6033    | invalid\_request\_error                            | Path parameters are required                                                           |
| 6034    | invalid\_request\_error                            | Endpoint path not configured correctly                                                 |
| 6035    | invalid\_request\_error                            | Configuration must include apiType field                                               |
| 6036    | invalid\_request\_error                            | API type not supported                                                                 |
| 6037    | invalid\_request\_error                            | Match type not allowed                                                                 |
| 6038    | invalid\_request\_error                            | The secret requested for deletion is already deleted                                   |
| 6039    | invalid\_request\_error                            | Tag must contain exactly one item                                                      |
| 6040    | invalid\_request\_error                            | Only portal owner can set portalId tag                                                 |
| 6041    | invalid\_request\_error                            | Not allowed to create secret                                                           |
| 6042    | invalid\_request\_error                            | Tag must include either portalId or portfolioId                                        |
| 6043    | invalid\_request\_error                            | Vault data not created                                                                 |
| 6044    | invalid\_request\_error                            | Vault data not created                                                                 |
| 6045    | invalid\_request\_error                            | Invalid IP address                                                                     |
| 6046    | invalid\_request\_error                            | {resource} not in required status                                                      |
| 6047    | invalid\_request\_error                            | {resource} already in requested state                                                  |
| 6048    | invalid\_request\_error                            | {resource} status requested not allowed                                                |
| 6049    | invalid\_request\_error                            | PortfolioID has to be for a portfolio in your sphere (not your own)                    |
| 6050    | invalid\_request\_error                            | "{resource}" title already exists                                                      |
| 6051    | invalid\_request\_error                            | No users for portfolio ID: {portfolioId}                                               |
| 6052    | invalid\_request\_error                            | {resourceIdField} already exists                                                       |
| 6053    | invalid\_request\_error                            | Attribute name cannot be empty                                                         |
| 6054    | invalid\_request\_error                            | All match fields must be a valid search field                                          |
| 6055    | invalid\_request\_error                            | Sort order not allowed                                                                 |
| 6056    | invalid\_request\_error                            | All sort fields must be a valid response field                                         |
| 14001   | required\_icc\_list\_or\_icc\_collection\_criteria | ICC collection can be static or dynamic                                                |
| 14002   | missing\_icc\_list                                 | Missing ICCIDs                                                                         |
| 14003   | iccid\_not\_in\_sphere                             | ICCIDs are not in sphere                                                               |
| 14004   | get\_snapshot\_file\_error                         | Unable to get snapshot file                                                            |
| 14005   | create\_snapshot\_file\_error                      | Unable to create snapshot file                                                         |
| 16000   | invalid\_request\_error                            | SIM is suspended                                                                       |
| 16001   | invalid\_request\_error                            | Missing iccPortfolioPackage assignment                                                 |
| 16002   | invalid\_request\_error                            | Attribute already exists                                                               |
| 16003   | invalid\_request\_error                            | Cannot make updates if portfolio is deleted                                            |
| 16004   | invalid\_request\_error                            | PackageId cannot be null                                                               |
| 16005   | invalid\_request\_error                            | Package not linked to portfolio                                                        |
| 16006   | invalid\_request\_error                            | Package not active in the portfolio                                                    |
| 16007   | invalid\_request\_error                            | MNOId of the ICCID being requested does not match the MNOId of the destination package |
| 16008   | invalid\_request\_error                            | MSISDN not tied to a portfolio or not found                                            |
| 16009   | invalid\_request\_error                            | MSISDN not tied to your portfolio                                                      |
