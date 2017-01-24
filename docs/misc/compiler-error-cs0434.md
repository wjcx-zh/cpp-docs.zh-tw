---
title: "編譯器錯誤 CS0434 | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0434
NamespaceName2 中的命名空間 NamespaceName1 與 NamespaceName3 中的類型 TypeName1 衝突  
  
 當匯入的類型與匯入的巢狀命名空間具有相同的完整名稱時，就會發這個錯誤。 參考該名稱時，編譯器將無法區分兩者。 如果您可以變更匯入的原始程式碼，您可以變更類型或命名空間的名稱，使兩者在組件內都是唯一的，來解決此錯誤。  
  
 下列程式碼會產生錯誤 CS0434。  
  
## 範例  
 這段程式碼會先建立具有相同完整名稱之類型的第一個複本。  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## 範例  
 這段程式碼會建立具有相同完整名稱之類型的第二個複本。  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## 範例  
 這段程式碼會參考具有相同完整名稱的類型。  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```