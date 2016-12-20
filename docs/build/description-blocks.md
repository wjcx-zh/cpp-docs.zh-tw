---
title: "描述區塊 | Microsoft Docs"
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
  - "區塊, description"
  - "描述區塊"
  - "NMAKE 程式, 描述區塊"
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 描述區塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述區塊是一個相依性行，後面可以選擇性地跟著命令區塊：  
  
```  
targets... : dependents...  
    commands...  
```  
  
 相依性行指定一個或多個目標，以及零或多個相依性。  目標必須位於行的開頭。  使用冒號 \(:\) 分隔目標和相依性，可以使用空格或定位字元。  若要分隔行，請在目標或相依性之後使用反斜線 \(\\\)。  如果目標不存在、具有比相依性早的時間戳記，或為[虛擬目標](../build/pseudotargets.md) \(Pseudotarget\)，NMAKE 就會執行命令。  如果相依性是其他處的目標且不存在，或相對於自身的相依性已經過時，NMAKE 將會在更新目前的相依性之前先更新該相依。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [目標](../build/targets.md)  
  
 [相依性](../build/dependents.md)  
  
## 請參閱  
 [NMAKE 參考](../build/nmake-reference.md)