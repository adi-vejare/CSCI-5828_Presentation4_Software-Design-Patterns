###Adapter Design Pattern
-	Used to make two incompatible interfaces to work together ie. adapts one to the other
-	For example, if we have a two pin plug and a three pin socket, we need an adapter to interface them or make them work together. Adapter design pattern works in the same way
-	It converts interface of one class into something that is accepted by another class
-	The following are the key terminologies in this pattern:
  + Target is the specific interface used by the client in consistency with its objects
  + Adaptee is the existing interface that required translation/adapting so that the client can interact with it
  + Adapter adapts/translates the adaptee to the target interface ie. essentially transating a client request to the adaptee
