
1) Adapter Design Pattern: Adapter design pattern is a design pattern that allows for two classes that have incompatible interfaces to be interfaced together by creating a wrapper around it. Similar to a charger adapter for a mobile phone that converts 240V main supply to be compatible with a device having much lower operating voltage such as a mobile phone (approx. 4-5V). This design pattern allows for polymorphism in a code and acts as a bridge by combining the capabilities of two independent interfaces.
2) The Adapter design pattern is used for situations where a source code update is not feasible or the source code shall not be modified. The client is presented with a level of abstraction and has no knowledge of whether a target or an adapter has been used.
The adapter design pattern solves problems like:
    a)How can a class be reused that does not have an interface that a client requires?
    b)How can classes that have incompatible interfaces work together?
    c)How can an alternative interface be provided for a class?
Often an (already existing) class can't be reused only because its interface doesn't conform to the interface clients require.
The key idea in this pattern is to work through a separate adapter that adapts the interface of an (already existing) class without changing it.

For example, a certain client is expecting a TextFormat functionality, that converts all fullstops to newline charecters. Assuming the input to this client comes from a csv file and comes with csvFormatter , that converts all fullstops to commas(','). therefore, we create an adapter so that the output of the csvFormatter maybe used by the TextFormatter.

class textFormat:

    txt = '\0'
    newTxt='\0'
    def newlines(self):
        self.newTxt=self.txt.replace('.','\n')
        return self.newTxt
    def __init__(self, string):
        self.txt=string
        
class csvFormat:

    txt = '\0'
    newTxt = '\0'
    def newlines(self):
        self.newTxt=self.txt.replace('.',',')
        return self.newTxt
    def __init__(self, string):
        self.txt=string
       
class AdaptCsvToTextFormat(csvFormat):
    
    def __init__(self, string):
        csvFormat.__init__(self,string)
    
    def newlines(self):
        self.newTxt=self.txt.replace('.','\n')
        return self.newTxt
        
Advantages of Adapter pattern are:
    1) Reusability and Flexibility.
    2) No modification of Source code.
    3) Abstraction provided -> customer only gets end interface.
Disadvantages:
    1) Many adaptations maybe required increasing code complexity.
