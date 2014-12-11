
##Introduction [DRAFT]

This document discusses strategies for integrating apps with other apps and building app 'ecosystems'. 

First let us consider why an ecosystem of apps is desirable.

App developers may find further uses for the data generated in other apps. When apps permit users to 'share' their data other apps could repurpose the data in different ways. Developers can focus on a particular domain where their app excels and allow other apps to deal with the related but separate problems, rather than trying to develop a toolbox that does everything. 

The 'blank slate' describes a common problem where a new app could be well designed and potentially useful but lacks 'content'. The app's value may rely on having a critical mass of existing data with which the user can interact. App promoters are often caught in a catch-22 where they need users to sign up to begin adding content, but find it difficult to convince potential users to do so when this initial content doen't exist. By connecting and importing data from other apps the app could 'seed' enough content and demonstrate value to users.

Users may have political or privacy concerns and wish to host their own a data themselves or with a group they trust. In the Web's current state multiple private providers host and control user data and 'experience'. Where these providers provide a 'free' service they typically sell advertising, or onsell user data to advertisers to sustain the business. A discussion of the private control of the Web vs the movement to shift control back to the users themselves is beyond the scope of this document. Suffice to say that many people are not satisfied with the Web in its current state (including us!).

By connecting apps to other apps and data held in the commons it seems possible to shift control of the web back to users without compromising on the more salient aspects of their experience (the amount and quality of data available) 

Lastly, with a conected ecosystem of apps users could avoid some of the more mundane tasks of the Web such as re-enetring details in various forms. 

-----

Four different strategies for integrating apps with other apps come to mind:
 1. 'Point-to-point Integration',
 2. 'Central Hub',
 3. 'Intergration as a Service', and
 4. 'Open Vocab'

We argue that 'Open Vocab' Strategy promotes more democratic and scalable app 'ecosystems' compared to the other options.

Next we discuss how app developers can progresively implement an Open Vocab strategy. 

Finally, we make specific API reccomendations for app's that wish to integrate with our 'Open App Ecosystem' using Loomio, Cobudget and DemcracyOS as examples.  


##Strategies for App Ecosystems

The main problem for any integration strategy is that developers inevitably represent the same or similar data in their apps in different ways. Developers call these representations 'models'.

For example, user account details are stored in a model known as a [User](https://github.com/loomio/loomio/blob/master/app%2Fserializers%2Fuser_serializer.rb) in Loomio, but in DemocracyOS the same concept is known as a [Citizen](https://github.com/DemocracyOS/app/blob/development/lib/models/citizen.js). Further, these models have similar properties but are specified with slightly different terminology. In DemocracyOS a 'Citizen' includes the following properties:

```
firstName:
lastName:
username:
avatar:
createdAt:
updatedAt:
profilePictureUrl:
disabledAt:
... 
```

While in Loomio a User includes the following:

```
name:
username:
avatar_initials:
avatar_kind:
avatar_url:
profile_url:
... 
```

Both of these include the term ```username``` which is undoubtedly the same concept. Other properties use different terms e.g. ```profile_url``` (Loomio) is the same concept as ```profilePictureUrl``` (DemocracyOS) while the 'name' concept is specified as ```name``` in Loomio but split across ```firstName``` and ```lastName``` in DemocracyOS. Humans can recognise ```profile_url``` and ```profilePictureUrl``` as the same concept but machines are not so smart! Further complications can arise when from different specifications. Dates and time data might have the same property name ```createdAt``` but use different date formats. 

###Point-to-point Integration

Where developers follow a 'Point-to-point Integration' strategy they must write specific *translation layers*for transforming models in one app into models in another. A Loomio feature that allows users to 'Import your account details from DemocracyOS' would require a 'translation layer' for transforming a Citizen model into a Loomio User model. This may not be so difficult in itself, but problems can arise if either of these apps make changes to their models or the number of these kinds of connections grow: 

![](https://www.mulesoft.com/sites/default/files/integration-complexity_2.png)

###Central Hub

The 'Central Hub' strategy puts the onus of connecting and writing translation layers on the other apps that want to connect with you! Clearly, this is only viable if your app is a market leader and controls access to desirable data. Twitter, Facebook and other well-known apps have succesfully used this strategy to create a surrounding 'ecosystem' of apps. This strategy is quite simple:

	1. Become a market leader.
	2. Maintain a useful, easy to use API.

Well, perhaps #1 is not so simple. 

A surrounding ecosystem is popular as it gives market leaders certain advantages. Every app that connects and relies on the Hub's API has the incentive for the Hub app to maintain its leading positon. These other apps will perhaps also do their own marketing and promote your app by proxy.

###Integration as a Service

A number of ventures offer [Integration (Platform) as a Service](https://www.mulesoft.com/resources/cloudhub/integration-as-a-service). The integration platform translates data from market leaders into their own representation. Apps need only connect once to the platform and purchase integration with several leading apps as package deals.

###Open Vocab

App developers collaborate to create a common, open vocabulary* and use this voabulary in their API's. For example, the OpenVocab team has specified the same User concept decribed above as a ['Person'](https://github.com/openvocab/person/blob/master/index.js) with the following properties:
```
name:
handle:
bio:
location:
avatar:
homepage:
memberships:
groups:
```

When apps use the same vocabulary, a feature that imports data from one app can work for any ther app that also uses the same vocabulary. Further, with linked data (discussed below) these terms reference others in existing standard vocabularies, meaning that these features will work for data stored in apps that are not *directly* in (or even aware of) the ecosystem. In fact, if apps decide to use a linked data format they are not required to use precisely these terms, only to link to the same term at its source vocabulary.


*also known as an [ontology](http://en.wikipedia.org/wiki/Ontology_(information_science))

###Discussion

### Linked Data and Open Vocab Implemention Strategies


##User

##Group

##Membership

##Motion 

##Vote