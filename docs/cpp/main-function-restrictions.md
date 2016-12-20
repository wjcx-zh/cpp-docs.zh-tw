---
title: "main 函式限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Main"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "main 函式, 使用限制"
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# main 函式限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**main** 函式的數個限制不適用於其他的 C\+\+ 函式。  **main** 函式：  
  
-   不能進行多載 \(請參閱[多載](../misc/overloading-cpp.md)\)。  
  
-   不可以宣告為 **inline**。  
  
-   不可以宣告為 **static**。  
  
-   無法取得自己的位址。  
  
-   不能被呼叫。  
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)