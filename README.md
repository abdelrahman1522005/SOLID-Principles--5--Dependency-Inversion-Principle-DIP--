# SOLID-Principles--5--Dependency-Inversion-Principle-DIP--
#Abstractions should not depend upon details. Details should depend upon abstractions

class FrontEnd:
  def __init__(self, back_end):
    self.back_end = back_end
  def display_data(self):
    data = self.back_end.get_data_from_database()
    print("Display data:", data)class BackEnd:
  def get_data_from_database(self):
    return "Data from the database

#In this example, the FrontEnd class depends on the BackEnd class and its concreteimplementation. You can say that both classes are tightly coupled. This coupling canlead to scalability issues. For example, say that your app is growing fast, and youwant the app to be able to read data from a REST API. How would you do that?


from abc import ABC, abstractmethod
class FrontEnd:
  def __init__(self, data_source):
    self.data_source = data_source
  def display_data(self):
    data = self.data_source.get_data()print("Display data:", data)
class DataSource(ABC):
  @abstractmethod
  def get_data(self):
    pass
class Database(DataSource):
  def get_data(self):
    return "Data from the database"
class API(DataSource):
  def get_data(self):
    return "Data from the API"
#In this redesign of your classes, you’ve added a DataSource class as an abstractionthat provides the required interface, or the .get_data() method. Notehow FrontEnd now depends on the interface provided by DataSource, which is anabstraction.
