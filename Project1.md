## Social Distancing Detector
### **Walt Disney World Magic Kingdom** Orlando, FL

[![Watch the video](https://user-images.githubusercontent.com/67920563/87249657-43028600-c42e-11ea-964b-f7d95e21cb7e.png)](https://youtu.be/a-UxJ6-qEpU)

Please Click Video for Viewing.

1. Was your social distance detector effective at detecting potential violations?
  - The detector seemed to accurately gauge the distance of people near the camera. However, there are visible erros in detection on the sides of the screen and further away. Originally, I had chosen a live stream of a Las Vegas casino. Because the detector classified objects such as casino slot machines as people, I was unable to effectively implement the detector on that video. This video had less objects, and thus was more successful. Although it missed people under the shadows, people that were too far away, and people in wheelchairs, the detector was sufficiently effective, but not perfect.
  - The detector is formatted to detect violations of social distancing between two people. However, the majority of people in the video are clustered in groups of friends or family. Although the families were not committing violations, the detector added them in the final count. 

2. Do you think this approach would be effective for estimating new infections in real time?  How would you implement such an approach in response to the COVID-19 
pandemic we are currently experiencing?
  - This approach does not seem to be an effective way for estimating new infections without improvement. In order to make this detector estimate infections, infected people would need to be detected or chosen at random. In order to detect those with coronavirus, a temperature check or COVID-19 test would need to be implemented before the people walked into the frame. Since this is logistically a pain to implement on a wide scale and can be very expensive, it is better to choose random people to carry COVID. For example, if it was known that there are an average 10 infections per 5,000 people, then the machine could select 1 person every 500 people to have the virus. The detector could then track the social distance infractions that person committed and thus count how many new possible infections could occur. With a sample big enough, it could potentially estimate infections. 
  
3. What limitations or improvements might you include in order to improve your proposed design?
