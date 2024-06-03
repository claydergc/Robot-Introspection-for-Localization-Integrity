202403181552

Status: #idea

Tags: [[Integrity]] [[Continuity]]

# Original Text

CONTINUITY
The continuity in the monitoring period is computed as:
$$\textrm{continuity}=1-\frac{\textrm{CTI}}{\textrm{MTBF}}$$

Where CTI is the continuity time interval (1hr in this case),
MTBF is the mean time between failures, which is computed as total time divided by number of failure events.

A failure event is counted as any period lasting for more than 10 seconds where:
HPL cannot be computed (i.e. <5 satellites in view above elevation mask);
Computed HPL > Alert Limit (i.e. 556m);
Computed horizontal position error > Alert Limit;
Any combination of the above.

It should be noted that continuity only considers failures due to unscheduled events, and so any periods of high HPL for example that have been previously informed via a NANU are not counted as a failure for continuity. During the monitoring period of July to September 2021 the following potential failure events were observed.
# In my own words

# References

[[@banfieldIntegrityContinuityAnalysis2021]]
