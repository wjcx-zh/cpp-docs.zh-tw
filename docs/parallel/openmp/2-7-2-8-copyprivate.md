---
title: "2.7.2.8 copyprivate | Microsoft Docs"
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
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.8 copyprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Copyprivate** 子句提供一個機制，來使用私用變數，從一個小組成員的值，廣播給其他成員。  它會提供共用的變數會難以 \(例如，在需要不同的變數，每個層級遞迴函式\) 時，使用共用的變數值的替代方法。  **Copyprivate** 子句只能出現在**單一**指示詞。  
  
 語法 **copyprivate** 子句是，如下所示：  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 則程式 **copyprivate** 變數在其變數清單中的子句相關聯的結構化區塊的執行後，就會發生**單一**建構，以及任何執行緒在小組中已離開障盾建構的結尾之前。  然後，在每個變數中的小組中的所有其他執行緒在*變數清單*，該變數就會變成 \(如同所定義工作分派\) 的執行緒執行建構的結構化的區塊中對應的變數值。  
  
 若要限制 **copyprivate** 子句如下：  
  
-   變數中所指定 **copyprivate** 子句必須出現在**私用** 或  **firstprivate** 子句對同一個**單一**指示詞。  
  
-   如果**單一** 指示詞與  **copyprivate** 在平行區域的動態範圍發生子句，所有變數中所都指定 **copyprivate** 子句必須是私用在封入的內容。  
  
-   變數中所指定 **copyprivate** 子句必須可存取的模稜兩可複製指派運算子。