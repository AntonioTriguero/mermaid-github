# mermaid-github
```mermaid
erDiagram
    %% V3 DATABASE

    programming ||--|| lms_courses : reference
    programming ||--|| session : contains
    session ||--|| lms_course_items : reference
    session ||--|| resource : contains
    resource ||--|| lms_lesson_items : reference
    group ||--|| resource : contains
    group {
        string id PK
        string name "NOT NULLABLE"
        int order "NOT NULLABLE"
    }
    resource {
        string id PK
        string session_id FK "NOT NULLABLE"
        string lesson_item_id FK "NOT NULLABLE"
        string group_id FK "NOT NULLABLE"
        int order "NOT NULLABLE"
        int resource_type "Enum: [session, sequence, annual, variable]" 
    }
    session {
        string id PK
        string course_item_id FK "NOT NULLABLE"
        string programming_id FK "NOT NULLABLE"
        int order "NOT NULLABLE"
    }
    programming {
        string id PK
        string course_id FK "NOT NULLABLE"
        string name "NOT NULLABLE"
        string description "NULLABLE"
        string status "Enum: draft, finished, published"
    }

    %% V2 DATABASE

    lms_lessons ||--|{ lms_lesson_items: contains
    lms_courses ||--|{ lms_course_items: contains
    lms_course_items {
        string guid PK 
        string course_guid FK "NOT NULLABLE"
    }
    lms_courses {
        string guid PK
    }
    lms_lessons {
        string guid PK
    }
    lms_lesson_items {
        string guid PK
        string lesson_guid FK "NOT NULLABLE"
    }

``
