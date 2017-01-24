---
title: "在函式和巨集之間選擇的建議 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.functions"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "函式 [CRT], 和巨集比較"
  - "巨集, 和函式比較"
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在函式和巨集之間選擇的建議
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分 Microsoft 執行階段程式庫常式為編譯或組譯的函式，不過有些常式會實作為巨集。  在標頭檔中宣告函式和常式的巨集版本時，巨集定義的優先順序最高，因為他永遠出現在函式宣告之後。  當您叫用實作為函式和巨集的常式時，您可以用兩種方式強制編譯器使用函式版本：  
  
-   將名稱放在括號內。  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   將「undefined」與 `#undef` 指示詞的巨集定義：  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 如果您需要在函式和程式庫常式的巨集實作之間選擇，請考慮下列交易：  
  
-   **Speed versus size** 使用巨集的主要優點是執行時間較快。  在前置處理中，每次使用時巨集展開 \(取代為其定義\) 內嵌。  不論有多少次呼叫，功能定義只發生一次。  巨集可以增加程式碼大小，但沒有額外負荷與函式呼叫。  
  
-   **函式評估** 評估位址的函式；巨集則否。  因此您無法仔需要指標的內容中使用巨集名稱。  例如，您可以宣告指標到函式，但不是指標到巨集。  
  
-   **Type\-checking** ，當您宣告函式時，編譯器會檢查引數型別。  由於您無法宣告巨集，編譯器無法檢查巨集引數型別：雖然它可以檢查傳遞給巨集的引數數目。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)