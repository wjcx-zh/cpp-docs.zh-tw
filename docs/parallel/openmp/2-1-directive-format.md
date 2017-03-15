---
title: "2.1 Directive Format | Microsoft Docs"
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
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.1 Directive Format
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在文法正式指定 OpenMP 指示詞的語法[附錄 c](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)，和非正式，如下所示：  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 每個指示詞開頭為 **\# pragma omp**，以減少潛在的衝突，具有相同名稱的其他 \(非 OpenMP 或廠商延伸 OpenMP\) pragma 指示詞。  指示詞的其餘部分會依照的編譯器指示詞的 c 和 C\+\+ 標準的慣例。  特別是，使用泛空白字元前後 **\#**，且有時必須使用空格來分開單字中的指示詞。  前置處理之後的語彙基元 **\# pragma omp** 受限於巨集取代。  
  
 指示詞是區分大小寫。  子句在指示詞中出現的順序並不重要的。  如有需要，在每個子句的描述中所列的限制，可能會重複出現在指示詞的子句。  如果*變數清單*就會出現在子句中，則必須指定只有變數。  只能有一個*指示詞名稱*可以指定每個指示詞。  例如，下列指示詞是不受允許:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP 指示詞適用於最多一個後續陳述，必須是結構化的區塊。