---
title: "2.7.2.3 lastprivate | Microsoft Docs"
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
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.3 lastprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`lastprivate`子句提供 \/m 所提供的功能的`private`子句。  語法`lastprivate`子句是，如下所示：  
  
```  
lastprivate(variable-list)  
```  
  
 控制台中的變數*變數清單*有`private`子句語意。  當`lastprivate`指示詞用來識別工作共用的建構，而每個值的子句便會出現`lastprivate`相關聯的迴圈中，或語彙上最後一個區段指示詞中，依序最後的反覆運算變數指派給變數的原始物件。  變數不會指派值的最後一個反覆項目**的** 或 **平行的**，或藉由語彙上最後一個區段的 **區段** 或 **平行區段**指示詞，建構之後，有一些未決定的值。  未指定的子物件也會有一些未決定的值建構後。  
  
 若要限制`lastprivate`子句如下：  
  
-   所有的限制，如`private`套用。  
  
-   與指定為類別型別變數`lastprivate`必須具有可存取的、 模稜兩可的複製設定運算子。  
  
-   變數，都是放在平行區域內私用或中顯示的`reduction`的子句**平行**指示詞不能在指定`lastprivate`工作共用的指示詞，以便繫結到平行建構函式上的子句。