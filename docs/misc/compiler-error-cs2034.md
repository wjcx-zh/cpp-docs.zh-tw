---
title: "編譯器錯誤 CS2034 | Microsoft Docs"
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
  - "CS2034"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2034"
ms.assetid: 72f2b785-ee23-4a1b-b12d-42d19c324d5e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2034
宣告外部別名的 \/reference 選項只能有一個檔名。 若要指定多個別名或檔名，請使用多個 \/reference 選項。  
  
 若要指定兩個別名及\/或檔案名稱，請使用兩個 **\/reference** 選項，如下所示：  
  
## 範例  
 下列程式碼會產生錯誤 CS2034。  
  
```  
// CS2034.cs // compile with: /r:A1=cs2034a1.dll;A2=cs2034a2.dll // to fix, compile with: /r:A1=cs2034a1.dll /r:A2=cs2034a2.dll // CS2034 extern alias A1; extern alias A2; using System;  
```