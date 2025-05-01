## Assignment 2

### Task 1 – Differential GNSS Positioning  
#### Deepseek
####  Prompt Used
Please give me some advices to compare the pros and cons of GNSS techniques, and I will give them setp-by-step.

Global Navigation Satellite Systems (GNSS) have transformed how smartphones determine location, but not all positioning techniques are equally suited for mobile navigation. Among the most widely used methods, Differential GNSS (DGNSS) strikes a practical balance for everyday use. By leveraging corrections from nearby reference stations, DGNSS improves accuracy to within 1–3 meters—far better than standard GNSS—without demanding excessive processing power. This makes it ideal for consumer applications like turn-by-turn navigation and location-based services. However, its reliance on base stations means performance degrades in remote areas, and it still struggles in urban canyons where signals are obstructed. While not as precise as more advanced techniques, DGNSS remains the most accessible and energy-efficient option for smartphones today.

For applications requiring extreme precision, Real-Time Kinematic (RTK) positioning stands out, offering centimeter-level accuracy by analyzing carrier-phase measurements in real time. This makes RTK invaluable for professional surveying, drone navigation, and autonomous vehicles. Some modern smartphones with dual-frequency GNSS chips can even utilize RTK corrections, unlocking high-precision tracking. However, the technology’s dependence on nearby base stations (typically within 20 km) limits its practicality for casual users. Additionally, the constant data streaming needed for corrections drains battery life quickly, and the infrastructure required makes widespread smartphone adoption challenging. While RTK is unmatched in accuracy, its current constraints prevent it from being a mainstream solution for mobile devices.

Precise Point Positioning (PPP) offers a compelling alternative by using global satellite corrections instead of local base stations, achieving decimeter-level accuracy after a convergence period. This makes PPP particularly useful in remote or maritime environments where reference stations are unavailable. However, its slow initialization—often taking 10–30 minutes—renders it impractical for real-time smartphone navigation. The computational load is also higher than DGNSS, which could strain mobile processors. Despite these drawbacks, PPP’s global coverage and improving correction services suggest it could play a bigger role in future smartphone navigation, especially as processing power increases and convergence times decrease.

The most promising advancement, however, may be PPP-RTK, which merges the best aspects of PPP and RTK. By incorporating atmospheric corrections and faster convergence algorithms, PPP-RTK can achieve near-instantaneous centimeter-level accuracy without requiring ultra-close base stations. This hybrid approach is particularly well-suited for smartphones, as it reduces dependency on local infrastructure while still delivering high precision. However, the technology remains complex, demanding significant processing power and reliable correction data streams—challenges that current smartphones are only beginning to address. As GNSS chips and correction services improve, PPP-RTK could eventually become the gold standard for mobile navigation, bridging the gap between high accuracy and everyday usability.

In summary, while DGNSS remains the most practical choice for smartphone navigation today, emerging techniques like PPP-RTK hold great potential for the future. As hardware advances and correction networks expand, smartphones may soon offer survey-grade precision, revolutionizing everything from pedestrian navigation to augmented reality applications. The key will be balancing accuracy with power efficiency and accessibility—ensuring these advanced GNSS methods enhance, rather than hinder, the mobile user experience.
### Task 2 – GNSS in Urban Areas  



### Task 3 – GPS RAIM (Receiver Autonomous Integrity Monitoring)  

### Task 4 – LEO Satellites for Navigation  
####  Prompt Used


### Task 5 – GNSS Remote Sensing  
####  Prompt Used



