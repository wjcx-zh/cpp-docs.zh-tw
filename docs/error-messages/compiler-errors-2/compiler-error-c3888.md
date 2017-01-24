---
title: "編譯器錯誤 C3888 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3888"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3888"
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3888
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name' : C\+\+\/CLI 不支援與這個常值資料成員關聯的常數運算式  
  
 使用[常值](../../windows/literal-cpp-component-extensions.md)關鍵字所宣告的*名稱*資料成員，是以編譯器不支援的值進行初始化。 編譯器僅支援常數整數、列舉或字串類型。**C3888** 錯誤的可能原因是資料成員使用位元組陣列進行初始化。  
  
### 更正這個錯誤  
  
1.  請檢查宣告的常值資料成員是支援的類型。  
  
## 請參閱  
 [literal](../../windows/literal-cpp-component-extensions.md)