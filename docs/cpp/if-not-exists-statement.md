---
title: "__if_not_exists 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__if_not_exists"
  - "__if_not_exists_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__if_not_exists 關鍵字 [C++]"
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __if_not_exists 陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`__if_not_exists` 陳述式會測試指定識別項是否存在。  如果識別項不存在，就會執行指定的陳述式區塊。  
  
## 語法  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`identifier`|要測試其是否存在的識別項。|  
|`statements`|如果 `identifier`  不存在，則會執行一個或多個陳述式。|  
  
## 備註  
  
> [!CAUTION]
>  為取得最可靠的結果，使用 `__if_not_exists` 陳述式時請遵循下列條件約束。  
  
-   只能將 `__if_not_exists` 陳述式套用至簡單類型，而不能套用於範本。  
  
-   將 `__if_not_exists` 陳述式套用至類別內外的識別項。  勿將 `__if_not_exists` 陳述式套用至區域變數。  
  
-   只在函式本體中使用 `__if_not_exists` 陳述式。  在函式的主體之外，`__if_not_exists` 陳述式只能測試完整定義的類型。  
  
-   當您對多載函式進行測試時，無法對特定形式的多載進行測試。  
  
 `__if_not_exists` 陳述式的補數是 [\_\_if\_exists](../cpp/if-exists-statement.md) 陳述式。  
  
## 範例  
 如需如何使用 `__if_not_exists` 的範例，請參閱 [\_\_if\_exists 陳述式](../cpp/if-exists-statement.md)。  
  
## 請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\_\_if\_exists 陳述式](../cpp/if-exists-statement.md)