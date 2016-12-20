---
title: "2.6.3 barrier Directive | Microsoft Docs"
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
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.3 barrier Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**障盾**指示詞會同步處理小組中的所有執行緒。  會發生，小組中的每一個執行緒等待直到所有的其他使用者已經達到這一點。  語法**障盾**指示詞時，如下所示：  
  
```  
#pragma omp barrier new-line  
```  
  
 小組中的所有執行緒所都遇到的障礙之後，小組中的每一個執行緒開始執行平行障盾指示詞之後的陳述式時。  請注意，因為**障盾**指示詞並沒有 c 語言陳述式做為其語法的一部分，有一些限制，在程式中的位置上。  請參閱 [＜ 附錄 c](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) 的正式的文法。  下列範例會示範這些限制。  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```