202403081714

Status: #idea

Tags: [[Integrity]] [[Dependability]]

# Original Text

A system's dependability is its ability to deliver a service that can justifiably be trusted. This notion encompasses three different concepts: (a) its attributes, the expected properties of the system, (b) its threats, unacceptable behaviors of the system that are causes or consequences of a lack of dependability, (c) its means, methods that allow a system to dependably perform its function (that is by placing a justified confidence in the service it delivers).

The attributes of dependability are properties that a system must verify. Six main attributes are dened: (a) Availability: readiness for correct service. (b) Reliability: continuity of correct service. A system is reliable if it delivers continuously and correctly its service for a specied period. (c) Maintainability: ability to undergo modications and repairs. It characterizes the ability of a system to be returned quickly from a failure to an operational state in which it can perform its required functions. (d) Safety: absence of catastrophic consequences on the user(s), the system, and the environment. (e) Condentiality: absence of unauthorized disclosure of information. (f ) Integrity: absence of improper system alterations. In this work we particularly focus on two attributes of dependability: safety and reliability. Note that trying to achieve both of these attributes may be contradictory. Indeed, for an autonomous vehicle in a dangerous situation, safety may require to stop and assess the situation, while reliability would ask to continue the performed service.

Threats are undesirable behaviors of the system. They are of three types: faults, errors and failures. These threats are linked by a causal relationship: the fault is the adjudged or hypothesized cause of an error, while the error is likely to result in a failure as shown in Figure 1. In this gure the decisional system A takes as input the output of the perception system B, so the correct service of A depends on the correct service of B. For A, the failure of B is considered as an external fault, which in turn can cause an internal error in A, then nally the failure of A. Perception in a robotic system being the basis upon which the system takes action, it is vital to avoid incorrect behavior, as failures could lead to the failure of the system as a whole.

![[Pasted image 20240308172046.png]]

Means have been designed to counter the previous threats. They are classied into four types: (a) Fault prevention, that is how to prevent the occurrence or introduction of faults in the system, (b) Fault tolerance, that is how to allow a system to properly fulll its function in the presence of faults, (c) Fault removal, that is how to reduce the presence (both number and severity) of faults in a system, (d) Fault forecasting, that is how to estimate the presence, the creation and consequences of faults in a system.
# In my own words

# References
[[@baderFaultTolerantArchitecture2017]]