---
title: "編譯器錯誤 CS0656 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0656
遺漏編譯器所需的成員 'object.member'  
  
 存在下列其中一個問題：  
  
-   Common Language Runtime 的安裝已損毀。  
  
-   您已參考組件，該組件定義的類型也在 Common Language Runtime 中發現。 不過，組件的類型定義方式不是 C\# 編譯器預期的方式。  
  
 請檢查您的參考，以確保使用正確的 Common Language Runtime 版本。