---
layout: default
title: Testing and Certification
has_children: true
nav_order: 40
---

# Testing Specifications


@startuml
'skinparam linetype polyline
'skinparam linetype ortho
hide circle
hide stereotype

'!pragma layout smetana

skinparam class<<RED>> {
 BorderColor DarkRed
 BackgroundColor MistyRose
 HeaderBackgroundColor #f09090
}
skinparam class<<GRAY>> {
 BorderColor DarkSlateGray
 BackgroundColor WhiteSmoke
 HeaderBackgroundColor #909090
}
skinparam class<<YELLOW>> {
 BorderColor #b07050
 BackgroundColor BUSINESS
 HeaderBackgroundColor #f2f295
}

skinparam class<<BLUE>> {
 BorderColor #505090
 BackgroundColor APPLICATION
 HeaderBackgroundColor SkyBlue
}

skinparam class<<GREEN>> {
 BorderColor DarkGreen
 BackgroundColor PHYSICAL
 HeaderBackgroundColor LimeGreen
}


    class "**Requirement**" as req<<GREEN>> {
        |_ requirement_id
        |_ requirement_status  
'        --
'        QuestionnaireResponse
        --
    }



package "Testing artifacts" as testing {


    class "**Test**\n** Criterium **" as crit<<YELLOW>> {
        |_ criterium_id
        |_ Specimen 
          |_ Collection Date  
          |_ Collection Place  
        --
'        Observation
    }


    class "**Test**\n** Scenario **" as scen<<YELLOW>> {
        |_ scenario_id
        |_ Specimen 
          |_ Collection Date  
          |_ Collection Place  
        --
'        Observation
    }

    class "**Test**\n** data set **" as tres<<YELLOW>> {
        |_ scenario_id
        |_ Specimen 
          |_ Collection Date  
          |_ Collection Place  
        --
'        Observation
    }
  }

    class "**Artifact**\n** Definition **" as prof<<YELLOW>> {
        |_ scenario_id
        |_ Specimen 
          |_ Collection Date  
          |_ Collection Place  
        --
'        Observation
    }


 

req "1..*" - "0..*" crit : "     "
crit "0..*" -r- "0..1" scen : "                "
scen "0..*" -d- "0..1" tres : "                "
prof "0..*" -r- "0..1" tres : "                "
req "0..*" -d[hidden]- "0..1" prof : "                "



caption

HIV Case Surveillance
endcaption
@enduml
