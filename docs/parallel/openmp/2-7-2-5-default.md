---
title: "2.7.2.5 default | Microsoft Docs"
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
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.5 default
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**預設**子句可讓使用者會影響資料共用屬性的變數。  語法**預設**子句是，如下所示：  
  
```  
default(shared | none)  
```  
  
 指定 **default\(shared\)** 相當明確列出每一個目前可見的變數，在**共用**子句，除非它是 **threadprivate** 或**缺點**`t`\-限定。  沒有明確使用**預設** 子句中，預設行為是相同 if  **default\(shared\)** 所指定。  
  
 指定 **default\(none\)** 需要至少一個下列必須為每一個參考給平行建構的語彙範圍中的變數，則為 true：  
  
-   變數會明確地列出資料共用屬性的子句中包含參考的建構。  
  
-   平行建構中宣告的變數。  
  
-   變數是 **threadprivate**。  
  
-   變數擁有 **const**\-限定型別。  
  
-   變數是迴圈控制變數的**的** 即為緊隨的迴圈 **的** 或 **平行的**指示詞，以及變數的參考會出現在這個迴圈。  
  
 指定變數在 **firstprivate**，  **lastprivate**，或 **降低**在封入的內容中被封入的指示詞的子句會使的隱喻參照給變數。  這類隱含參考也會隨著上面所列的需求。  
  
 只會有一個**預設** 子句指定 **平行**指示詞。  
  
 變數的預設資料共享的屬性可以藉由覆寫**私用**，  **firstprivate**，  **lastprivate**， **降低**，以及 **共用**子句，如下列範例所示範：  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```