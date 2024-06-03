202403151412

Status: #idea

Tags: [[gnss]] [[gps]] [[localization]]

# Original Text

When an airplane is flying, the GPS (Global Positioning System) receiver onboard receives data from a network of satellites orbiting the Earth. This data typically includes:

1. **Position Information:** The GPS provides the aircraft's latitude, longitude, and altitude, enabling precise navigation and tracking of its location in real-time.
    
2. **Time Information:** GPS satellites also transmit time signals, which are used by the GPS receiver to calculate the exact time with high precision. This is important for synchronization and timing of various navigation and communication systems on the aircraft.
    
3. **Velocity Information:** The GPS receiver can calculate the aircraft's ground speed and direction of travel (course) by analyzing the change in position over time.
    
4. **Satellite Data:** The GPS receiver receives information about the satellites in view, including their positions and signal health. This data is used to determine which satellites are best to use for calculating the aircraft's position.
    
5. **Differential GPS (DGPS) Corrections:** In some cases, the aircraft may receive correction signals from ground-based stations or satellite-based augmentation systems (SBAS) like WAAS (Wide Area Augmentation System) in the US, EGNOS (European Geostationary Navigation Overlay Service) in Europe, or MSAS (MTSAT Satellite Augmentation System) in Japan. These corrections improve the accuracy of the GPS position information.
    
This data allows the aircraft to accurately navigate, maintain its course, and ensure safe and efficient flight operations.

Yes, the concept of Integrity Risk (IR) is important in the context of aircraft navigation, particularly when using Global Navigation Satellite Systems (GNSS) such as GPS. Integrity in this context refers to the trust that can be placed in the correctness of the information provided by the navigation system. It's a measure of the system's ability to provide timely warnings to users when the system should not be used for navigation.

Integrity Risk (IR) is a quantitative measure of the risk that the navigation system's information is incorrect without providing a timely warning. This risk is critical for safety-of-life applications, such as aviation, where relying on incorrect position information could lead to catastrophic consequences.

In aviation, the required level of integrity is very high, and various standards and mechanisms are in place to ensure that the Integrity Risk is kept within acceptable limits. These include:

1. **Fault Detection and Exclusion (FDE):** This involves monitoring the signals from each satellite and detecting any anomalies or faults. If a fault is detected in a satellite signal, that satellite can be excluded from the position calculation.
    
2. **Receiver Autonomous Integrity Monitoring (RAIM):** This is a technique used by GNSS receivers to assess the integrity of the GNSS signals. RAIM can detect faults in the satellite signals and provide a warning to the user if the integrity of the position solution is in doubt.
    
3. **Satellite-Based Augmentation Systems (SBAS):** Systems like WAAS, EGNOS, and MSAS provide additional integrity information by monitoring the GNSS satellites and broadcasting correction and integrity information to users.
    
4. **Ground-Based Augmentation Systems (GBAS):** These systems provide very high accuracy and integrity by using ground-based reference stations to monitor GNSS signals and provide corrections and integrity information to aircraft in the vicinity of an airport.
    

The goal is to ensure that the probability of an undetected navigation error exceeding a certain threshold (which could lead to a hazardous situation) is extremely low, typically on the order of 10^-7 to 10^-9 per hour of flight, depending on the phase of flight and the specific requirements of the operation.

## Integrity Risk (IR)

Aircraft calculate Integrity Risk when using GNSS (Global Navigation Satellite System) through a combination of onboard systems and external augmentation services. One of the most common methods for assessing integrity in aviation GNSS applications is Receiver Autonomous Integrity Monitoring (RAIM). Here's a simplified example to illustrate how RAIM works:

### Example: RAIM for Integrity Monitoring

Suppose an aircraft is using a GNSS receiver with RAIM capability to navigate. The receiver is tracking signals from multiple satellites to determine the aircraft's position. For the sake of this example, let's assume the receiver is tracking six satellites.

1. **Fault Detection:** RAIM uses redundant satellite measurements to detect potential faults. With six satellites, the receiver can compute a position solution using different combinations of five satellites. This process is repeated multiple times, each time excluding a different satellite from the calculation. If one of these combinations yields a significantly different position estimate, the excluded satellite is suspected to be faulty.
    
2. **Fault Exclusion:** Once a faulty satellite is identified, it can be excluded from the position calculation. The receiver then recalculates the position using the remaining satellites.
    
3. **Integrity Risk Assessment:** The receiver assesses the integrity risk by evaluating the consistency of the position solutions obtained from different satellite combinations. If the solutions are consistent, the integrity risk is considered low. If there are inconsistencies, the integrity risk is higher, and the receiver may provide a warning to the pilot.
    
4. **Warning Threshold:** The receiver has predefined thresholds for acceptable integrity risk levels. If the assessed integrity risk exceeds these thresholds, the receiver will provide a warning to the pilot indicating that the GNSS position information should not be used for navigation.
    

For example, during an approach phase of a flight, the RAIM algorithm might require that at least five satellites are available for position calculation, with one additional satellite for integrity monitoring (a total of six satellites). If the algorithm detects that excluding any one satellite results in a position error greater than a certain threshold (e.g., 10 meters), it will flag an integrity alert, indicating that the GNSS information may not be reliable.

It's important to note that this is a simplified example, and actual RAIM implementations can be more complex, taking into account various factors such as satellite geometry, signal quality, and receiver design. Additionally, in modern aviation, aircraft often use Satellite-Based Augmentation Systems (SBAS) like WAAS or EGNOS, which provide additional integrity information and improve the accuracy and reliability of GNSS positioning.

## Obtaining positions from satellites

In GNSS (Global Navigation Satellite System), each individual satellite does not give you a position directly. Instead, the position is determined by combining signals from multiple satellites. This process is known as trilateration. Here's a simplified explanation:

1. **Distance Measurement:** Each satellite continuously transmits signals that contain information about its location and the current time. When your GNSS receiver picks up the signal, it calculates how long the signal took to travel from the satellite to the receiver. Since the signal travels at the speed of light, the receiver can use this time to calculate the distance to the satellite.
    
2. **Trilateration:** To determine your position, the receiver needs to know the distance to at least three satellites. With two satellites, you can narrow down your location to two points, but you need a third satellite to pinpoint your exact position. This is because the intersection of three spherical surfaces (each centered at a satellite and with a radius equal to the distance to that satellite) is a single point in three-dimensional space.
    
3. **Number of Positions:** If you have access to three satellites, you can obtain one position. Each additional satellite can provide more information to improve the accuracy of the position estimate and allow for additional calculations like velocity or integrity monitoring.
    
4. **Four or More Satellites:** In practice, GNSS receivers typically use signals from four or more satellites. The fourth satellite is necessary to determine the receiver's clock offset (since the receiver's clock is not as precise as the atomic clocks on the satellites). This clock offset is used to correct the time measurement, which in turn improves the accuracy of the distance calculations and the final position estimate.
    

So, in summary, with three satellites, you can obtain one position. However, for practical and accurate GNSS positioning, signals from at least four satellites are typically used.

## Grouping satellites

Q: If I have 4 satellites called s1, s2, s3 and s4; can I group them in s1, s2, s3 and s2, s3, s4 to obtain one position from each group, i.e. 2 positions?

Technically, you can group satellites in different combinations to obtain multiple position solutions, but in practice, this is not how GNSS receivers typically operate. Instead, they use all available satellites simultaneously to compute a single, more accurate position.

In your example, you have four satellites: s1, s2, s3, and s4. You could theoretically use the combinations (s1, s2, s3) and (s2, s3, s4) to compute two separate positions. However, each of these positions would be less accurate than a position computed using all four satellites together. This is because more satellites provide better geometric diversity, which improves the accuracy of the position solution.

Furthermore, GNSS receivers are designed to use as many satellites as possible to improve not only the accuracy but also the reliability and integrity of the position solution. If one satellite's data is faulty or if the signal is temporarily lost, the receiver can still compute an accurate position using the remaining satellites.

In summary, while you can theoretically group satellites to obtain multiple positions, in practice, GNSS receivers use all available satellites to compute a single, more accurate position.

## Consistent information among satellites

When I say "if solutions are consistent," I'm referring to the agreement or similarity between the position solutions obtained from different combinations of satellites. In the context of Receiver Autonomous Integrity Monitoring (RAIM) or other integrity assessment methods, a GNSS receiver might compute multiple position solutions using different subsets of the available satellites. This is done to detect potential errors or faults in the satellite signals.

For example, suppose a receiver is tracking signals from five satellites. It could compute several position solutions using different combinations of four out of those five satellites. If all these solutions are very close to each other (i.e., the differences between them are within a small tolerance), then the solutions are considered consistent. This consistency indicates that there is likely no significant error or fault in the satellite signals being used, and thus the integrity risk is considered low.

On the other hand, if one of these solutions is significantly different from the others, it suggests that there might be an error in the signal from the satellite that was excluded in that particular solution. In this case, the solutions are considered inconsistent, and the integrity risk is higher. The receiver might then issue a warning indicating that the GNSS position information may not be reliable.

## Computing integrity in the industry

The industry standard for computing integrity for commercial airplanes, particularly for satellite-based navigation systems like GPS, is defined by the requirements for the Receiver Autonomous Integrity Monitoring (RAIM) and the more advanced Fault Detection and Exclusion (FDE) algorithms. These standards are specified by organizations such as the International Civil Aviation Organization (ICAO) and the Federal Aviation Administration (FAA).

RAIM is a technology used in GPS receivers to assess the integrity of the GPS signals and ensure that the navigation solution provided is reliable. It works by using redundant satellite measurements to detect and flag any satellite signal errors that could compromise the accuracy of the position fix. RAIM is a requirement for certain phases of flight where precision is critical, such as non-precision approach procedures.

FDE is an extension of RAIM that not only detects faults but also identifies and excludes the faulty satellite from the position solution, allowing for continued use of the GPS for navigation even in the presence of a satellite anomaly.

The specific requirements for RAIM and FDE, including the performance parameters and integrity thresholds, are detailed in standards such as:

1. **ICAO Annex 10** (Aeronautical Telecommunications) - Provides international standards and recommended practices for aeronautical telecommunications, including navigation systems.
2. **RTCA DO-229** (Minimum Operational Performance Standards for Global Positioning System/Wide Area Augmentation System Airborne Equipment) - Specifies the minimum performance requirements for GPS and WAAS receivers used in aviation, including integrity monitoring.
3. **RTCA DO-178** (Software Considerations in Airborne Systems and Equipment Certification) - Provides guidance for the development and certification of aviation software, including software used in integrity monitoring systems.

These standards ensure that the integrity of the navigation solution meets the safety requirements for commercial aviation, allowing pilots and air traffic controllers to trust the accuracy and reliability of the position information provided by the aircraft's navigation system.

# In my own words

# References