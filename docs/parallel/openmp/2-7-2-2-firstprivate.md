---
title: "2.7.2.2 firstprivate | Microsoft Docs"
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
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.2 firstprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Firstprivate** 子句提供 \/m 所提供的功能的**私用**子句。  語法 **firstprivate** 子句是，如下所示：  
  
```  
firstprivate(variable-list)  
```  
  
 控制台中的變數*變數清單* 有 **私用** 子句語意，如所述 [區段 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 在 25\] 頁面上。  如同它已執行過一次每個執行緒，要建構的執行緒執行之前，會發生初始設定或建構。  對於 **firstprivate** 上的平行建構函式的子句，新的私用物件的初始值是將遇到的執行緒的平行建構之前存在於原始物件的值。  對於 **firstprivate** 子句的工作共用建構函式上，每個執行緒執行工作共用的建構新的私用物件的初始值是原始物件之前相同的執行緒遇到工作共用的建構的時間點上存在的值。  此外，C\+\+ 物件，新的私用物件，每個執行緒是由原始物件所組成的複本。  
  
 若要限制 **firstprivate** 子句如下：  
  
-   在指定的變數 **firstprivate** 子句必須沒有不完整型別或參考型別。  
  
-   與指定為類別型別變數 **firstprivate** 必須可存取的、 模稜兩可的複製建構函式。  
  
-   變數，都是放在平行區域內私用或中顯示的**降低** 的子句 **平行** 指示詞不能在指定  **firstprivate** 工作共用的指示詞，以便繫結到平行建構函式上的子句。