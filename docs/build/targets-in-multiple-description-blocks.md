---
title: "多重描述區塊中的目標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "區塊, 多個描述"
  - "描述區塊"
  - "多個描述區塊"
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 多重描述區塊中的目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用不同的命令，更新在一個以上描述區塊中的目標，請在目標與相依之間指定兩個連續冒號 \(::\)。  
  
```  
target.lib :: one.asm two.asm three.asm  
    ml one.asm two.asm three.asm  
    lib target one.obj two.obj three.obj  
target.lib :: four.c five.c  
    cl /c four.c five.c  
    lib target four.obj five.obj  
```  
  
## 請參閱  
 [目標](../build/targets.md)