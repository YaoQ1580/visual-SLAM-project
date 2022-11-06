# visual SLAM

**1.	Introduction**

**1.1	Background**

Anji Logistics company wanted to develop an Automatic Guided Vehicle (AGV) which can navigate a factory by using Simultaneous Localization And Mapping (SLAM) technology. Specifically, the AGV was mounted a camera and this camera continuously took pictures of surrounding environment. By putting these pictures into Rtabmap (a SLAM software), the AGV can know its position in the factory.

The Rtabmap software contains two phases. The first phase is called mapping phase, during which the AGV navigates around the factory while taking pictures of surrounding environments, and then all the pictures and motor positions where these pictures are taken are stored in the Rtabmap and Rtabmap will generate a map of the factory, as depict in Fig 1.

![image](https://user-images.githubusercontent.com/67689632/200152281-9d10a785-92f2-4042-b094-c5bc54f65364.png)
Fig 1

The second phase is called localization phase, during which the AGV can navigate freely through the factory, and Rtabmap will use the map information generated in phase one to calculate accurate position of the AGV. This position information can then be further put into a route planning algorithm called moveBase so that when a user sends commands of moving to a specific location, the AGV can figure out the best path to reach that location. This phase is depicted in Fig 2.

![image](https://user-images.githubusercontent.com/67689632/200152285-61351805-9054-4770-88b6-2bc7121c1146.png)
Fig 2

**1.2	Problem**

In phase 2, the positions calculated by Rtabmap have many errors and vary a lot, as depicted in Fig 3. The dotted line is the map generated in phase one and the solid line is the locations generated by Rtabmap during phase two.

![image](https://user-images.githubusercontent.com/67689632/200152289-710ce7b2-1120-4825-a7e5-0b403372d8ff.png)
Fig 3

**2.	My work**

my work is to figure out the causes of these errors. There are many factors which can influence the accuracy of the computed position. I studied the Rtabmap code and the mathematical principles behind the algorithm used to calculate positions, and finally I found three critical factors and did a lot of experiments to compare the result of different sets of factors, as depicted in Fig 4.

![image](https://user-images.githubusercontent.com/67689632/200152300-825b583f-7cbe-41e3-9321-1977ca209b8e.png)
![image](https://user-images.githubusercontent.com/67689632/200152304-f62c79b7-52c9-4a49-94da-ad6f44cceb03.png)
![image](https://user-images.githubusercontent.com/67689632/200152307-824c2408-09e1-4ae7-af34-66d3aa9120b2.png)
Fig 4

**3.	Result**

Finally, I found a relatively good set of configuration parameters of Rtabmap which can let the software output the positions of the AGV with tolerable errors, as depicted in Fig 5.

![image](https://user-images.githubusercontent.com/67689632/200152311-5ad6c317-8257-423c-9fc3-ed99fc622ffd.png)
Fig 5
