---
title: "連結器工具警告 LNK4092 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4092"
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 連結器工具警告 LNK4092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

共用的可寫入區段 'section' 含有重新配置，映像可能無法正確執行  
  
 當您擁有共用區段，連結器就會發出這個警告，警告您可能會有潛在的嚴重問題。  
  
 要在多個處理序之間共用資料的方法之一，就是將一個區段標示為「共用」。然而，將區段標示為共用可能會造成問題。  例如，您的 DLL 在共用資料區段中包含一個像這樣的宣告：  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 連結器無法解析 `pvar`，因為它的值將由該 DLL 在記憶體的載入位置決定，因此它會在 DLL 中放置一個重新配置記錄。  當 DLL 載入到記憶體時，`var` 的位址便可解析，`pvar` 的位址也會完成指派。  如果其他處理序也載入同一個 DLL 但卻無法載入於相同位址，則 `var` 位址的重新配置就會更新為第二個處理序，而第一個處理序的位址空間會指向錯誤的位址。