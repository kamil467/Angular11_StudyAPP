### 1. How DI implemented in Angular ?
ANS: DI system is integral part of Angular framework.
#
2. What is Injector ?
ANS: Injector is responsible for creating and injecting services into angular application.
When angular application bootstrapped , it creates two types of injector.
1. Module injector - created for each module in angular app.
2. Elements injector- created for every component and destroyed when component destroyed.

Angular maintains injector tree hierarchy similar to componenet tree.
If any component expected dependency , first the request will send to attached component's injector. It will resolve if it is registered , otherwise the request 
will forward to parent injector. It will go until module as it is parent of components.
#

#### 3. What is the use of Injectable decorator ?
We should use if our service is dependent on any other service. This will tell Angular about constructor meta data information.
#

#### 4. What is providerIn ?
it is an object which links DI token with instance.
We are registering in injector that for this DI token , injector supposed to provide instance of this type.


#### 5. How do you create Singleton object in Angular ?
decorate the service with providerIn as root.


