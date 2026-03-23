# Hurricane-Related Network Outage Recovery

## Context
Following a nationwide hurricane (Melissa) that disrupted power and communications infrastructure across Jamaica, most surrounding homes regained internet access, once grid power was restored. However, my home network remained offline while neighboring connections using the same ISP were functional. This document outlines the assessment process and resolution steps taken to restore connectivity following the disaster.

## Initial Symptoms
The modem powered on normally with solid Power and DS/US indicators, but the Online LED continued blinking and never fully registered. All connected devices showed “Connected without Internet,” despite stable power and confirmed service availability in nearby homes.

## Constraints
The issue occurred during post-hurricane recovery when infrastructure stability was uncertain. There was ISP support delays due to widespread outage recovery, and time pressure to restore connectivity for my studies. Service restoration needed to be achieved using basic troubleshooting methods.

## Assessment & Reasoning
Initial assessment focused on determining whether the issue was within the home network or external to it. Stable power, intact cabling, and identical behavior across multiple devices ruled out internal wiring, Wi-Fi, or device-specific faults. Direct Ethernet testing produced the same “connected but no internet” result, indicating the problem was not wireless-related. These checks pointed to an incomplete modem synchronization with the ISP network rather than a local hardware failure.

## Actions Taken
Performed a physical reset of the modem by holding down the reset button for approximately 15 seconds to clear stale configuration and force re-registration with the ISP network. Allowed a 15-minute stabilization period for automated provisioning and configuration refresh to complete.

## Outcome
After the reset and automated provisioning cycle completed, the modem Online LED turned solid and downstream/upstream channels bonded successfully. All connected devices regained stable internet access, confirming service restoration.

## Lessons Learned
This incident reinforced the importance of methodical troubleshooting during post-disaster recovery. Verifying power, cabling, and device behavior before escalation helped isolate the fault domain quickly. It also highlighted that automated ISP provisioning delays can persist after widespread outages, and that a controlled modem reset can safely trigger re-registration when local conditions are stable.
