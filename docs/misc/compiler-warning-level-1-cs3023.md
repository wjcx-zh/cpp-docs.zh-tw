---
title: "編譯器警告 (層級 1) CS3023 | Microsoft Docs"
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
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3023
CLSCompliant 屬性在套用至傳回類型時沒有任何意義，  請改放在方法上。  
  
 由於 CLS 符合性規則套用至方法和類型宣告，因此不會檢查函式傳回類型是否符合 CLS 標準。  
  
## 範例  
 下列範例會產生警告 CS3023：  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```