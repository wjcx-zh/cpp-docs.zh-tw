---
title: "累計相依性 | Microsoft Docs"
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
  - "相依性累計"
  - "NMAKE 中的累計相依性"
  - "相依性"
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 累計相依性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果重複目標，相依性是在描述區塊中累積。  
  
 比方說，這組規則，  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 評估如下︰  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 指定每個已在不同的描述區塊中，但不是最後一個相依性列中的目標不會使用命令區塊，會評估單一描述區塊中的多個相依性程式碼行中的多個目標。 NMAKE 會嘗試使用這類目標的推斷規則。  
  
 比方說，這組規則，  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 評估如下︰  
  
```Output  
  
leap.exe : jump.obj  
# invokes an inference rule  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
## <a name="see-also"></a>另請參閱  
 [目標](../build/targets.md)