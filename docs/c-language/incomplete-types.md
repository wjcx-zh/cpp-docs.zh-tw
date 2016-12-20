---
title: "不完整的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "陣列 [C], 不完整的類型"
  - "不完整的類型"
  - "結構, 不完整的"
  - "類型 [C], 不完整的"
  - "等位, 不完整的"
  - "void 關鍵字 [C]"
  - "void 關鍵字 [C], 不完整的"
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 不完整的類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不完整類型是一種描述識別項的類型，但缺少判斷識別項大小所需的資訊。  「不完整類型」可以是：  
  
-   您尚未指定成員的結構類型。  
  
-   您尚未指定成員的等位類型。  
  
-   您尚未指定維度的陣列類型。  
  
 void 類型是一種無法完成的不完整類型。  若要完成不完整類型，請指定遺漏的資訊。  下列範例顯示如何建立和完成不完整類型。  
  
-   若要建立不完整的結構類型，請宣告一個結構類型，但不指定其成員。  在此範例中，`ps` 指標會指向名為 `student` 的不完整結構類型。  
  
    ```  
    struct student *ps;  
    ```  
  
-   若要完成不完整的結構類型，請於稍後使用其指定的成員在相同範圍中宣告相同的結構類型，如下所示  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   若要建立不完整的陣列類型，請宣告一個陣列類型，而不指定其重複計數。  例如：  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   若要完成不完整的陣列類型，請於稍後使用其指定的重複計數在相同範圍中宣告相同的名稱，如下所示  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## 請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)