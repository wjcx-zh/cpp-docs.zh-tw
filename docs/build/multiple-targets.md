---
title: "多重目標 | Microsoft Docs"
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
helpviewer_keywords: 
  - "目標的 makefile"
  - "NMAKE 中的多個目標"
  - "多重 NMAKE 中的目標"
  - "NMAKE 程式目標"
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多重目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 評估單一相依性中的多個目標，每個不同的描述區塊中指定。  
  
 例如，這個...  
  
```Output  
bounce.exe leap.exe : jump.obj  
   echo Building...  
```  
  
 ..來評估如下︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building...  
leap.exe : jump.obj  
   echo Building...  
```  
  
## <a name="see-also"></a>另請參閱  
 [目標](../build/targets.md)