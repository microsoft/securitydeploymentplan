```mermaid       
            flowchart LR
                %% Core components
                subgraph Core["Zero Trust Core"]
                    Zero["Zero Trust Security Suite"]
                    Foundation["Zero Trust Foundation"]
                    Data["Data Protection"]
                    Threats["Threat Defense"]
                end

                %% Core relationships
                Foundation --> Zero
                Data --> Zero
                Threats --> Zero

                %% Add click events for core components
                click Zero "https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview" _blank
                click Foundation "https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview" _blank
                click Data "https://learn.microsoft.com/en-us/purview/data-protection" _blank
                click Threats "https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender" _blank

                %% Key Components
                subgraph KeyIdentity["Foundation"]
                    CloudID["Cloud Identity"]
                    MFA["MFA"]
                    CA["Conditional Access"]
                    IntuneEnroll["Device Enrollment"]
                    IntuneCompPol["Compliance Policies"]
                end
                CloudID --> MFA
                MFA --> CA
                CA --> Foundation
                IntuneEnroll --> IntuneCompPol
                IntuneCompPol --> CA

                %% Add click events for Foundation components
                click CloudID "https://learn.microsoft.com/en-us/entra/fundamentals/whatis" _blank
                click MFA "https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks" _blank
                click CA "https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview" _blank
                click IntuneEnroll "https://learn.microsoft.com/en-us/mem/intune/enrollment/" _blank
                click IntuneCompPol "https://learn.microsoft.com/en-us/mem/intune/protect/device-compliance-get-started" _blank

                subgraph KeySecurity["Threat Protection"]
                    XDR["M365 Defender XDR"]
                    MDVM["Defender VM"]
                    DID["Defender Identity"]
                    MDE["Defender Endpoint"]
                    MDCA["Defender Cloud Apps"]
                end
                DID --> XDR
                MDE --> XDR
                MDCA --> XDR
                XDR --> Threats
                MDVM --> Threats

                %% Add click events for Threat Protection components
                click XDR "https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender" _blank
                click MDVM "https://learn.microsoft.com/en-us/defender-vulnerability-management/" _blank
                click DID "https://learn.microsoft.com/en-us/defender-for-identity/what-is" _blank
                click MDE "https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint" _blank
                click MDCA "https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps" _blank

                subgraph KeyData["Data"]
                    DSPM["Purview DSPM"]
                    EndpointDLP["Endpoint DLP"]
                end
                DSPM --> Data
                EndpointDLP --> Data

                %% Add click events for Data Protection components
                click DSPM "https://learn.microsoft.com/en-us/purview/data-security-posture-management" _blank
                click EndpointDLP "https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about" _blank

                %% Styling
                classDef deployed fill:#90EE90,stroke:#333,stroke-width:2px
                classDef notDeployed fill:#FFB6C1,stroke:#333,stroke-width:2px
                classDef subgraphStyle fill:#f5f5f5,stroke:#666,stroke-width:2px
                classDef core fill:#e1f5fe,stroke:#0277bd,stroke-width:3px

                %% Apply styles
                class Core,KeyIdentity,KeyEndpoint,KeySecurity,KeyData subgraphStyle
                class Zero,Foundation,Data,Threats core

```