```mermaid
classDiagram
Couse_Data --> Course_Info
Couse_Data : Text Course
Couse_Data : Text name
Couse_Data : Int CRN
Couse_Data : Text Type
Couse_Data : Text Section
Couse_Data : Text Day
Couse_Data : Text Location
Couse_Data : Text Instructor

User_data <-- Course_Info : NetID
User_data : Text Name
User_data : Text Email
User_data: Text Major 
User_data: Text NetId 
```

2edwad
