## Social Distancing Detector
### **Walt Disney World Magic Kingdom** Orlando, FL

[![Watch the video](https://user-images.githubusercontent.com/67920563/87249657-43028600-c42e-11ea-964b-f7d95e21cb7e.png)](https://youtu.be/a-UxJ6-qEpU)

Please Click Video for Viewing. Video taken from [Live Stream](https://youtu.be/wNRgYXF-sZA)

### Discussion

1. Was your social distance detector effective at detecting potential violations?
  - The detector seemed to accurately gauge the distance of people near the camera. However, there are visible erros in detection on the sides of the screen and further away. Originally, I had chosen a live stream of a Las Vegas casino. Because the detector classified objects such as casino slot machines as people, I was unable to effectively implement the detector on that video. This video had less objects, and thus was more successful. Although it missed people under the shadows, people that were too far away, and people in wheelchairs, the detector was sufficiently effective, but not perfect.
  - The detector is formatted to detect violations of social distancing between two people. However, the majority of people in the video are clustered in groups of friends or family. Although the families were not committing violations, the detector added them in the final count. 

2. Do you think this approach would be effective for estimating new infections in real time?  How would you implement such an approach in response to the COVID-19 
pandemic we are currently experiencing?
  - This approach does not seem to be an effective way for estimating new infections without improvement. In order to make this detector estimate infections, infected people would need to be detected or chosen at random. In order to detect those with coronavirus, a temperature check or COVID-19 test would need to be implemented before the people walked into the frame. Since this is logistically a pain to implement on a wide scale and can be very expensive, it is better to choose random people to carry COVID. For example, if it was known that there are an average 10 infections per 5,000 people, then the machine could select 1 person every 500 people to have the virus. The detector could then track the social distance infractions that person committed and thus count how many new possible infections could occur. With a sample big enough, it could potentially estimate infections. In order to make this even more accurate, the distance from the infected person to the others could be calculated, and probabilites of each person on the screen catching the virus could be calculated. For example, if the infected person is touching someone and is three inches away from them, that person would have a 70% chance of being contaminated. Meanwhile, the person furthest away from the infected being would have a 3% chance of being infected. If one added mask detection, that could raise or lower your chances of being infected.

3. What limitations or improvements might you include in order to improve your proposed design?
  - Because of the problem cited in answer one regarding the false violations committed by groups of people, I would make a second detector which consolidated people withing six inches of each other as one unit. This second detector would undershoot the amounts of social distancing infractions while the current one overshoots infractions. I would then conduct a test to estimate the error in each detector. In order to get a final estimation of total infections, I would average the two numbers of infections based on their respective weights. For example, if Detector 1 had more error than Detector 2, the average would be skewed more towards the number of infections in Detector 2. 
  - In order to solve the problem with classification of objects as people, I would train the detector more. I would collect data beforehand to see if there are certain objects which the machine will tend to confuse with people, and then use that data to make a more accurate detector. 
  - Because distance, object, and darkness distort people, I would perhaps consider adding a feature that detects heat. Thus, my machine would be more certain of where it needs to be detecting people.
  - Another improvement to the machine would be to track movements and sound that are related to coughing or sneezing. Since coughing and sneezing can increase the amount of particles released into the air and inhaled by others, tracking those movement could help more accurately detect infections. 
  - I think a lot of people don't know how to gauge six feet. If this could be implemented through satellite and broadcasted onto people's phones/smartwatches wherever they go, people might be more cautious if they receive alerts of violations. It could be like your own Social Distancing GPS!
  
  *Disclaimer: All numbers used in the above questions are ficticious and only used for proof of concept.
