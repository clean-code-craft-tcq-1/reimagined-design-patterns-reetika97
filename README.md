# reimagined-design-patterns

Give a summary description of Four design patterns that you choose from the following design patterns: **Adapter,  Builder, Composite, Decorator, Observer, Interpreter, State, Mediator, Memento, Prototype, Proxy**. In your summaries say:

- what kind of problem(s) you can solve with that pattern and when you use it, maybe with a short example
- how the pattern works, what the basic idea of the pattern is
- what the main advantage and what the the main disadvantage is of using this pattern
- Write a short summary for each of the four patterns, about half a page for each pattern (rather less than more). 

> Do not add diagrams, and do not try to give a complete description of the patterns as found in the books. Rather think of how you would explain the essential ideas of these patterns in a few sentences to a colleague while drinking coffee.
> 

1) Adapter Design Pattern: Adapter design pattern is a design pattern that allows for two classes that have incompatible interfaces to be interfaced together by creating a wrapper around it. Similar to a a charger adapter for a mobile phone that converts 120V main supply to be compatible with a much lower voltage mobile phone (approx. 4-5V). This design pattern allows for polymorphism in a code and acts as a bridge by combining the capabilities of two independent interfaces.
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
        
