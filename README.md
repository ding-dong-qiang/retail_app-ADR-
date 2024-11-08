# retail_app-ADR
Group members:
Dong Chen
Manminder Singh
Ngoc Tam Nguyen
Within your group, discuss the following architectural decisions (AD):
Scenario 1:
You are a team responsible for developing a new mobile app for a retail company. The app will allow customers to browse and purchase products, view their order history, and track the status of their deliveries. Additionally, the app will have a loyalty program feature, where customers can earn and redeem points for discounts on future purchases. The following requirements must be considered:
APP Requirement:
•	To browse and purchase products
•	View their order history
•	Track the status of their deliveries
•	Redeem points for discounts in the future
•	Support offline mode, allowing customers to browse products and view their order history even when they are not connected to the internet.
•	The app should sync data with the server once an internet connection is available
•	Send push notifications to customers to notify them about order updates, new product arrivals, and exclusive offers
•	Integrate with various payment gateways
•	Track user behavior (as product views, purchases, and loyalty program interactions.) Which to help improve the app's performance and user experience
•	Display product images, which may vary in size and resolution such as caching
•	The app should support multiple languages and adapt to various cultural preferences

1/ Native, web, or hybrid app: 
•	Issue / Context: The retail company wants to make a mobile app. It can browse and purchase products. In addition, the mobile app can integrate with various payments gateways, track user behavior and support various languages.
Name	Description	Pros	Cons
NATIVE	The applications that built for specific platforms by using specific language for it 	•	Better performance as it is dedicated to one kind of operating system
•	More reliable security	•	Maintaince required 
•	Long time for Development
WEB	The application that built for web by using the concepts and languages of the web development 	•	Browser is responsible for most of the things 
•	Does not affect the performance of the system	•	Only applicable on web browsers 
•	Canno be accessed in offline mode 
HYBRID	The application which is mixture of both WEB and NATIVE it sounds like cross platform application in a way 	•	Use features from both web and native platform
•	Can be accessed in offline mode too	•	Big role of third-party applications 
•	Performance is not consistent 
•	Decision: We decided to choose a hybrid app because it can use platforms such as web, Android app, and iOS app.

RATIONALE:
•	It is more powerful than other two platforms
•	More Customizable 
•	Considered faster platform for developing applications 
 
•	Consequence: the size of the application is big and complex to maintain. In addition, synchronicity of the framework needs a lot of time between versions.
•	It will limit the performance of the application 
•	User experience will get affected 

2/ UI Framework: 
•	Context: The UI framework should support online and offline. It allows customers to browse products and view their order history.
Name 	Description	Pros 	Cons
FLUTTER	Framework which is developed by google and used for making applications for both web and mobile  	Consistent UI
Performance is great	Limited support for the UI plat forms
Dart is not easy language to handle 
REACT-NATIVE	Framework which is developed by Facebook and use JavaScript as language to develop applications 	Large Community to support

JavaScript makes easy for developers to handle things 	Performance is not optimized
Debugging is hard as it also supports cross plat form 
NATIVE - SCRIPTS	Framework which uses JavaScript, and it depends on the various APIs to make environment like native	Can use Multiple Frameworks at one time 

APIs make things easier and way more simple 	Performance is the biggest concern of this UI
Accessible to very few plugins and libraries opposite to the react native


•	Decision:
 We decided to go with react native as a UI

RATIONALE:
•	It offers both online and offline functionality and it comes with plenty of libraries and plugins which can help developers to add the required functions in an efficient way an Moreover, the users will also understand the workflow of application easily on the other hand if company will use flutter then developers will have to come up with compatible JDK and flutter versions which is not easy to make both synchronized.

Consequence:
•	React native comes with react native dependencies which are heavy and will increase the size of the application in the end 
•	Deprecated features by node will be one of the main issues 
•	Debugging will require high end system

3/ Backend language:
•	Context: Our group needs to choose  NodeJS combined with a relationship database such as MariaDB, or Oracle or non-relationship as MongoDB. That’s used to store product, order and customer information as well.

•	Decision options:
	Pros	Cons
NodeJS	Support JSON: it works well with data JSON and response the request retrieve data between front-end and back-end.
Easy sync data with front-end through API.
 	Depend on third-party library: it uses package library for connecting to the database with difference versions so it can not sync between versions.
Complex maintenance source because it uses many libraries such as Exxpresses or package to connect to the database.
MariaDB	Scalability: it easy to deploy on cloud platform such as AWS or Google Cloud.
Maintainability: it organized simple data such table and support multiple columns which helps to maintain easily.
Security: it provide ability data encryption for mobile app.	Complex upgrade versions: every version MariaDB require different configuration so it’s different when moving data between version.
MongoDB	Scalability: it supports sharding data between servers and sync data from sharding easy. 
Maintainability: easy back-up because it support through MongoDB local and MongoDB Atlas.
Security: it supports high security through restrict access users.
	Complex with big database because it doesn’t use the relationship database. 
•	Final decision: We decided to choose MongoDB combine with NodeJS for back-end of the application.
•	RATIONALE: 
It can sync easy and flexible with to support offline mode data and sync when it connect to Internet.
•	Consequence: MongoDB uses non-relationship databases so it can get mistake for duplicate data when saving it. 

4/ Permissions:
•	Context: Our group want to push notifications to users when discounts or new products. That’s helps to increase interaction and attraction of users. We should choose possible permissions to use.
•	Decision options:



	Pros	Cons
Notification permission 	Allows to push notification. It is useful reminder and alert to users.	Make distract users when using the application.
Store/file permission	Allows to read files from storage devices	Increase size file saving on devices.
Camera permission	Allows capture photos and video from the application.	User confusing about risk security personal data.

•	Final Decision: We decided to use notification permission 
•	RATIONABLE:
To push offers or new products to customers. In addition, we use store/file permissions to save local data and sync when it connects to the Internet.

•	Consequence: The push notifications can not send if users don’t allow the permission on their device.

5/ Data storage:
•	Decision title: Data Storage Strategy for Retail Mobile App with Offline Mode
•	Context: The retail mobile app requires a robust data storage strategy to support essential functionalities such as product browsing, purchasing, order tracking, and a loyalty program.
•	Decision Options:
	Pros	Cons
Local Storage	Securely store sensitive information like authentication tokens and payment preferences.	Keeping data consistent between local storage and the server can be challenging, especially if changes are made while offline.
Cloud storage	Cloud storage can synchronize data in real time or near real time, ensuring that users always have access to the latest product information, order statuses, and loyalty points across all devices.	Despite strong security measures, cloud storage is still vulnerable to potential breaches.
Hybrid Solutions	A hybrid approach combining local and cloud storage allows the app to work seamlessly offline and synchronize once online.	If users make changes offline (e.g., updating their profile, adding items to a wish list) and then go online, the app must handle potential conflicts between offline and cloud-stored data.

•	Decision: We decided to utilize hybrid solutions as our data storage strategy.
•	Rationale：
A hybrid approach, combining cloud storage for scalability and real-time updates with local storage for offline access, might balance these advantages and mitigate the drawbacks. This hybrid solution allows users to browse products and view order history offline while still benefiting from cloud-based features like data synchronization, analytics, and secure storage for sensitive data.
•	Consequence:
Improved User Experience: Users can access product catalogs and order histories offline, enhancing accessibility and reliability.
Complex Development: Syncing and conflict resolution between local and cloud storage will increase development complexity, requiring additional resources for coding, testing, and maintenance.

6/ Selection of Payment Gateway:
ADR
•	Decision Title: Selection of Payment Gateway or service provider to integrate
•	Context: our team needs to choose a payment gateway or combination based on supported regions, transaction fees, and security standards (e.g., Stripe, PayPal, or Adyen). You may need to integrate different gateways for international users.
•	Decision Options: 
	Pros	Cons
Stripe	Developer-Friendly: Stripe is known for its extensive API and detailed documentation, making it highly customizable and easy to integrate for developers. It’s a preferred choice for businesses needing flexible and tailored payment solutions.	Complexity for Smaller Businesses: For small businesses or teams without dedicated developers, Stripe’s extensive customization options can feel overwhelming.
PayPal	High User Trust: PayPal is a trusted brand worldwide, and many users already have PayPal accounts, which can lead to a higher conversion rate as customers feel comfortable paying via PayPal.	Higher Fees: PayPal typically charges a higher transaction fee (e.g., 2.9% + 30¢ in the U.S. and higher for international transactions) and additional fees for currency conversions.
Adyen	Global Enterprise Solution: Adyen supports over 200 payment methods and is available in more than 150 currencies, making it a top choice for large, international companies like Uber and Spotify.	Less Developer-Friendly: Compared to Stripe, Adyen’s developer tools and documentation are less accessible for smaller businesses without dedicated tech teams.


•	Final Decision: we decided to take Stripe as our payment gateway.
•	Rationale: 
Stripe is generally a better option due to its ease of setup and lower complexity. Stripe offers flexibility and a customizable API, while PayPal’s trust factor and ease of use may lead to higher customer conversion.
•	Consequences: 
Customer Support Limitations: Stripe primarily provides support via email and chat, without immediate phone support for standard accounts. This can lead to delays when resolving critical issues, which may impact the customer experience if users encounter problems during payment.
