## Assignment 2

**Name:** ZHANGDi 24046964R

**Date:** 12 March 2025  

### Task 1 – Differential GNSS Positioning  
```  
Model: Deepseek
Prompt: Could you please advise me on how to contrast the advantages and limitations of different GNSS techniques? I would like to focus on the following four methods: Differential GNSS (DGNSS), Real-Time Kinematic (RTK), Precise Point Positioning (PPP), and PPP-RTK. Specifically, I’m looking to understand their differences in terms of positioning accuracy, convergence time, infrastructure requirements, and suitability for various remote sensing or geophysical applications, such as GNSS seismology.
```  


Global Navigation Satellite Systems (GNSS) have transformed how smartphones determine location, but not all positioning techniques are equally suited for mobile navigation. Among the most widely used methods, Differential GNSS (DGNSS) strikes a practical balance for everyday use. By leveraging corrections from nearby reference stations, DGNSS improves accuracy to within 1–3 meters—far better than standard GNSS—without demanding excessive processing power. This makes it ideal for consumer applications like turn-by-turn navigation and location-based services. However, its reliance on base stations means performance degrades in remote areas, and it still struggles in urban canyons where signals are obstructed. While not as precise as more advanced techniques, DGNSS remains the most accessible and energy-efficient option for smartphones today.

For applications requiring extreme precision, Real-Time Kinematic (RTK) positioning stands out, offering centimeter-level accuracy by analyzing carrier-phase measurements in real time. This makes RTK invaluable for professional surveying, drone navigation, and autonomous vehicles. Some modern smartphones with dual-frequency GNSS chips can even utilize RTK corrections, unlocking high-precision tracking. However, the technology’s dependence on nearby base stations (typically within 20 km) limits its practicality for casual users. Additionally, the constant data streaming needed for corrections drains battery life quickly, and the infrastructure required makes widespread smartphone adoption challenging. While RTK is unmatched in accuracy, its current constraints prevent it from being a mainstream solution for mobile devices.

Precise Point Positioning (PPP) offers a compelling alternative by using global satellite corrections instead of local base stations, achieving decimeter-level accuracy after a convergence period. This makes PPP particularly useful in remote or maritime environments where reference stations are unavailable. However, its slow initialization—often taking 10–30 minutes—renders it impractical for real-time smartphone navigation. The computational load is also higher than DGNSS, which could strain mobile processors. Despite these drawbacks, PPP’s global coverage and improving correction services suggest it could play a bigger role in future smartphone navigation, especially as processing power increases and convergence times decrease.

The most promising advancement, however, may be PPP-RTK, which merges the best aspects of PPP and RTK. By incorporating atmospheric corrections and faster convergence algorithms, PPP-RTK can achieve near-instantaneous centimeter-level accuracy without requiring ultra-close base stations. This hybrid approach is particularly well-suited for smartphones, as it reduces dependency on local infrastructure while still delivering high precision. However, the technology remains complex, demanding significant processing power and reliable correction data streams—challenges that current smartphones are only beginning to address. As GNSS chips and correction services improve, PPP-RTK could eventually become the gold standard for mobile navigation, bridging the gap between high accuracy and everyday usability.

In summary, while DGNSS remains the most practical choice for smartphone navigation today, emerging techniques like PPP-RTK hold great potential for the future. As hardware advances and correction networks expand, smartphones may soon offer survey-grade precision, revolutionizing everything from pedestrian navigation to augmented reality applications. The key will be balancing accuracy with power efficiency and accessibility—ensuring these advanced GNSS methods enhance, rather than hinder, the mobile user experience.

### Task 2 – GNSS in Urban Areas  

To begin the analysis, the navSolutionResults.mat file—generated from the “Urban.dat” dataset in Assignment 1—is loaded to retrieve essential GNSS navigation data. This includes information such as pseudorange measurements, satellite positions, satellite clock corrections, and corresponding timestamps for each epoch. These data serve as the foundation for further processing and accuracy enhancement in GNSS localization.

Next, the Skymask data is loaded from a CSV file (e.g., skymask_A1_urban.csv). The Skymask provides environmental information regarding potential signal obstructions around the GNSS receiver, especially relevant in urban canyon scenarios. Specifically, it records the minimum elevation angle at which satellite signals can be received as a function of azimuth angle. This allows us to determine which satellite signals are likely to be blocked due to surrounding buildings or obstacles.

Upon loading the Skymask file, a polar plot or 2D graph is generated where the azimuth angle (in degrees) is represented on the x-axis and the corresponding blocking elevation angle (in degrees) is represented on the y-axis. This plot visually illustrates the angular regions of the sky where satellite visibility is restricted. Such information is critical for identifying non-line-of-sight (NLOS) satellite signals, which can degrade positioning accuracy if not properly accounted for.


<img src="https://github.com/user-attachments/assets/e832f09b-1c24-45f6-a435-33991e4009b5" alt="image" width="400">

Subsequently, the Skymask data is processed by applying a correction to the elevation angles, thereby generating the final Skymask profile used for satellite visibility assessment.

<img src="https://github.com/user-attachments/assets/52baf193-a2a5-4f7c-9219-89f5e358a2ec" alt="image" width="400">




### Task 3 – GPS RAIM (Receiver Autonomous Integrity Monitoring)  
The consistency of GPS signals received from multiple satellites can be evaluated using the Receiver Autonomous Integrity Monitoring (RAIM) algorithm. RAIM enhances reliability by cross-checking the measurements from different satellites and detecting any anomalies or inconsistencies in the data. If discrepancies are found, users are promptly alerted to potential integrity issues in the positioning solution. To implement RAIM, the GNSS navigation data is first loaded, and the RAIM algorithm is then integrated into the Weighted Least Squares (WLS) positioning framework, enabling real-time fault detection by monitoring the residuals of the position estimation process, showed in task3.m 

We have provided code to identify inconsistency in received GPS signals. The satellite positions throughout the entire data recording period are shown as follows:

<img src="https://github.com/user-attachments/assets/0e53e207-3ff5-4096-9c69-a092acb97f80" alt="image" width="400">

### Task 4 – LEO Satellites for Navigation
```  
Model: Deepseek
Prompt: What are the key difficulties and challenges in utilizing LEO communication satellites for GNSS navigation purposes, and how should we approach these technical considerations.
```  

Low Earth Orbit (LEO) satellites have revolutionized global communication, enabling high-speed internet and low-latency data transmission through constellations like Starlink and OneWeb. Given their rapid orbital movement and strong signal strength, researchers have explored whether these satellites could also support navigation, potentially complementing or even augmenting traditional Global Navigation Satellite Systems (GNSS). However, using LEO communication satellites for positioning introduces several technical and operational challenges that complicate their adoption as a reliable navigation solution.

One of the primary difficulties lies in the inherent design differences between LEO communication satellites and dedicated GNSS satellites. Traditional GNSS systems, such as GPS or Galileo, operate in Medium Earth Orbit (MEO), where their slower orbital speed and predictable trajectories allow for stable signal transmission and precise orbital modeling. In contrast, LEO satellites move at much higher velocities, completing an orbit in roughly 90 to 120 minutes. This rapid motion introduces significant Doppler shifts in their signals, which, while beneficial for detecting position changes, complicates signal processing and requires advanced algorithms to compensate for frequency variations. Additionally, because LEO constellations are primarily optimized for communication rather than navigation, their signals lack the precise timing and geodetic reference frameworks that GNSS signals provide, making accurate positioning more difficult to achieve.

Another major challenge is the lack of standardized navigation signals from LEO satellites. GNSS systems transmit well-defined signals with embedded timing and ephemeris data essential for calculating position. In contrast, LEO communication satellites broadcast signals designed for data transfer, not navigation. While researchers have demonstrated that these signals can be repurposed for positioning through techniques like time-of-arrival and Doppler shift measurements, the process requires extensive signal processing and external corrections. Furthermore, without synchronized atomic clocks—a staple of GNSS satellites—LEO-based positioning suffers from timing inaccuracies that degrade precision. Even with advanced signal processing, achieving meter-level accuracy comparable to GNSS remains difficult without additional infrastructure or hybrid systems combining LEO and traditional GNSS measurements.

The dynamic nature of LEO constellations also poses a challenge for continuous and reliable navigation. Unlike GNSS satellites, which follow well-defined orbits with long-term stability, LEO constellations frequently adjust their positions to maintain optimal communication coverage and avoid collisions. This means that satellites used for navigation at one moment may no longer be in a usable position minutes later, requiring constant updates to tracking algorithms. Moreover, because LEO satellites are much closer to Earth (typically 500–2,000 km altitude compared to GNSS at ~20,000 km), their signals cover smaller ground footprints. A user may lose connection as satellites quickly pass overhead, leading to intermittent positioning updates unless a dense constellation ensures continuous coverage. While companies like SpaceX have thousands of Starlink satellites in orbit, gaps in coverage can still occur, particularly in polar regions or during satellite handovers.

Atmospheric and environmental factors further complicate LEO-based navigation. While LEO signals are stronger than those from GNSS due to their proximity, they are also more susceptible to disruptions from weather, urban obstructions, and ionospheric interference. GNSS systems use dual-frequency signals to mitigate ionospheric delays, but most LEO communication satellites operate on single-frequency bands, making them more vulnerable to atmospheric errors. Additionally, the low elevation angles at which LEO satellites are often observed near the horizon increase the likelihood of signal blockage by buildings or terrain, reducing reliability in urban canyons or mountainous regions.

Despite these challenges, the potential benefits of LEO-based navigation—such as enhanced signal strength, faster geometric changes for quicker convergence, and resilience against GNSS jamming—continue to drive research in this area. Hybrid systems that combine LEO signals with GNSS or ground-based augmentation could mitigate some of the difficulties, offering improved accuracy and availability. However, for LEO communication satellites to become a viable standalone navigation solution, advancements in signal standardization, onboard atomic clocks, and dynamic orbit modeling will be necessary. Until then, their role in positioning is likely to remain supplemental rather than a replacement for traditional GNSS systems.

In conclusion, while LEO satellites present an intriguing opportunity to enhance global navigation capabilities, their current use for precise positioning faces significant hurdles. The fast-moving nature of LEO orbits, lack of navigation-optimized signals, constellation dynamics, and atmospheric vulnerabilities all contribute to the complexity of implementing a reliable LEO-based GNSS alternative. Future developments in satellite technology and signal processing may overcome some of these obstacles, but for now, traditional GNSS remains the gold standard for accurate and dependable navigation.


### Task 5 – GNSS Remote Sensing  
```  
Model: Deepseek
Prompt: PLease：
Analyze GNSS data for crustal deformation monitoring
Explore how high-precision GNSS measurements help detect tectonic plate movements and ground displacement before, during, and after earthquakes.

Integration with seismic networks
Discuss the advantages of combining GNSS with traditional seismometers to improve real-time earthquake detection and early warning systems.

Use of GNSS for tsunami early warning
Investigate how GNSS-derived vertical displacements in coastal areas can help identify tsunami-generating earthquakes.

Application in slow slip event detection
Examine how GNSS can reveal slow slip events that are not easily detectable by traditional seismology methods.

Contribution to earthquake hazard modeling
Evaluate how long-term GNSS data can be used to improve fault models and assess seismic hazards in high-risk regions.

GNSS networks in post-seismic analysis
Study the role of GNSS in observing post-seismic relaxation and understanding stress redistribution after major earthquakes
```
Global Navigation Satellite Systems (GNSS) have revolutionized geodetic monitoring by providing continuous, high-precision measurements of crustal deformation. Unlike traditional seismic sensors that detect ground shaking, GNSS directly measures displacement, making it indispensable for studying tectonic plate movements, earthquake cycles, and post-seismic relaxation. By analyzing GNSS time series data, scientists can detect millimeter-to-centimeter-level ground motions before, during, and after earthquakes, offering critical insights into fault behavior and stress accumulation. For example, in subduction zones like Japan and Cascadia, GNSS networks have recorded interseismic strain buildup, revealing locked zones where future earthquakes may occur. During large seismic events, real-time GNSS (RTK-GNSS or PPP) helps quantify coseismic slip distribution, which is crucial for rapid hazard assessment. Post-seismically, GNSS tracks afterslip and viscoelastic relaxation, improving our understanding of stress transfer and future earthquake potential.

A major advancement in earthquake monitoring is the integration of GNSS with traditional seismic networks. While seismometers excel at detecting high-frequency seismic waves, they saturate during very large earthquakes, limiting their ability to estimate fault slip magnitude in real time. GNSS, however, provides direct displacement measurements without saturation, enabling more accurate magnitude estimation for early warning systems. Countries like Japan and the U.S. have incorporated GNSS into their earthquake early warning (EEW) systems, significantly reducing false alarms and improving warning times. For instance, during the 2011 Tohoku earthquake, Japan’s GNSS-enhanced EEW system provided critical seconds of advance notice before strong shaking reached Tokyo. Combining GNSS with accelerometers and seismometers creates a more robust monitoring framework, enhancing real-time hazard assessment and disaster response.

GNSS also plays a vital role in tsunami early warning systems by detecting vertical crustal displacements associated with undersea earthquakes. Unlike seismic waves, tsunamis are generated by large-scale seafloor deformation, which GNSS can measure directly. In regions like Indonesia and Chile, coastal GNSS stations have been deployed to monitor sudden uplift or subsidence that may indicate a tsunami-triggering earthquake. For example, during the 2010 Maule earthquake in Chile, GNSS data helped confirm significant seafloor displacement, prompting timely tsunami warnings. Real-time kinematic (RTK) GNSS networks, such as those operated by NOAA and UNESCO’s Intergovernmental Oceanographic Commission, provide near-instantaneous data to tsunami warning centers, improving the speed and accuracy of alerts.

Another critical application of GNSS is the detection of slow slip events (SSEs), which are transient fault movements that release stress without generating significant seismic waves. These events, often occurring in subduction zones, were largely undetectable before the advent of high-precision GNSS. By analyzing subtle, long-term displacement patterns, scientists have identified recurring SSEs in regions like Cascadia and New Zealand, where they may influence the timing of future megathrust earthquakes. GNSS-derived strain rates help distinguish between locked, creeping, and slowly slipping fault segments, refining our understanding of earthquake cycles.

Long-term GNSS observations contribute significantly to earthquake hazard modeling by improving fault zone characterization. By accumulating decades of deformation data, researchers can estimate slip rates, locking depths, and strain accumulation along active faults. This information is integrated into probabilistic seismic hazard assessments (PSHAs), which guide building codes and disaster preparedness strategies. For example, in California, the Plate Boundary Observatory (PBO) GNSS network has been instrumental in refining the seismic hazard models for the San Andreas Fault system. Similarly, in the Himalayas, GNSS measurements have revealed strain partitioning between major thrust faults, helping assess future earthquake risks in densely populated areas.

Following major earthquakes, GNSS networks are essential for post-seismic analysis, tracking afterslip, and viscoelastic relaxation in the Earth’s crust. Afterslip, which occurs as the fault continues to adjust after the main rupture, can be precisely measured using continuous GNSS stations. This data helps scientists understand stress redistribution and potential triggering of adjacent faults. For instance, after the 2004 Sumatra earthquake, GNSS observations revealed prolonged afterslip and crustal readjustment across the Sunda Trench. Similarly, post-seismic GNSS data from the 2015 Gorkha earthquake in Nepal provided insights into lower-crustal viscosity and stress transfer mechanisms.

In conclusion, GNSS technology has become a cornerstone of modern earthquake and crustal deformation studies. Its ability to detect subtle ground motions—whether from tectonic strain, slow slip events, or post-seismic relaxation—complements traditional seismology and enhances hazard assessment. Integrated GNSS-seismic networks improve real-time earthquake and tsunami warnings, while long-term GNSS data refines fault models and seismic risk evaluations. As GNSS precision continues to improve and real-time processing becomes more widespread, its role in mitigating earthquake-related disasters will only grow, making it an indispensable tool in geohazard monitoring.




