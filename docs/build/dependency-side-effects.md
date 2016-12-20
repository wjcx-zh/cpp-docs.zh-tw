---
title: "相依性的副作用 | Microsoft Docs"
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
  - "相依性的副作用"
  - "NMAKE 程式，相依項目"
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 相依性的副作用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果以冒號 （:） 中不同的位置，兩個相依性程式碼行中指定的目標，而且命令會顯示其中一個程式碼行，NMAKE 就會解譯相鄰或合併時的相依性。 它不會叫用推斷規則的相依性，沒有任何命令，但卻會假設隸屬於一個描述區塊之相依性，以及執行其他相依性所指定的命令。 例如，此設定的規則︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 評估如下︰  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 如果雙冒號不會發生這種效果 (`::`) 使用。 例如，此設定的規則︰  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 評估如下︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>另請參閱  
 [目標](../build/targets.md)