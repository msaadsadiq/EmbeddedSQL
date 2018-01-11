# EmbeddedSQL

In this project we have been assigned the task to develop an airport information system to organize all information about all
the airplanes stationed and maintained at the airport in the XYZ county. We need to develop both the Conceptual and logical
diagrams while following the necessary design steps. Finally we implement the designed database in the ORACLE database
using SQL and run 10 test case queries using Embedded SQL. As a first step it is appropriate to specify the assumptions that
are used in our design
Following are the constraints and assumptions
– We assume that there is only one union and each employee is member of that union. Therefore the union name is
not worth mentioning. If there are more than one unions, then it would be necessary to create another entity called
'Union' that will hold the different unionNames and their disctinctive Ids.
– There can be several airplanes of the same model, for example, there can be several Boeing 737 airplanes with
different registration numbers.
– Each technician has an expertise of at least one airplane.
– A traffic controller cannot not also work as a technician, or vice versa.
– Each airworthiness test is performed by one technician only on one aircraft only using one test type only.
– If there are many technicians, there may be some technicians who have never conducted any test.
– There is at least one airplane of each model type. Otherwise why would the model be listed in the models table
– The FAA tests have a general list and it is not mandatory that each test have at least one plane linked to it. There
may be tests that are not required in the region.
– Every airplane has a Boolean attribute called 'airworthiness'. If the airplane fails its test, then the FAA can request
the airplane's airworthiness to be changed to False so it is grounded.
– Each test must be conducted by a technician who is an expert on that model.
– For a technician to be “conducting” a test, and for a technician to “be expert” for a given test and model are
two distinct relationships. We have no ER constraints that establishes such value-based relationships among 2
distinct relationships of “is-expert” versus “conducts-tests” and verifying that the matching technician entity
exists in both cases


Determination of candidate and primary key attributes of entity types.
Employee
Primary key: ssn
Candidate Key: ssn, unionMemNo
Technician
Primary key: ssn (FK Reference to Employee)
Candidate key: ssn, phone
Other attributes: name, salary, address
TechnicianExpertise
Primary key: ssn (FK Ref. To Technician), modelNo (FK Ref. To AirplaneModel)
Candidate key: ssn, modelNo
Other attributes: comments, yearSinceExpert
TrafficController
Pirmary key: ssn (FK Ref. To Employee), examDate
Candidate key: ssn, examDate
Other attributes: medExamScore
Airplanes
Primary key: regNo
Candidate key: regNo
Other attributes: airworthy, modelNo (FK Ref. Airplane Model)
AirplaneModel
Primary key: modelNo
Candidate key: modelNo
Other attributes: capacity, weight
TestType
Primary key: FAANo
Candidate key: FAANo, name
Other attributes: maxScore
TestConducted
Primary key: regNo(FK Ref. Airplane), modelNo,ssn (FK Ref. TechnicianExpertise), testNo(FK Ref. TestType)
Candidate key: regNo, modelNo, ssn, testNo
Other attributes: score, testDate, hours
