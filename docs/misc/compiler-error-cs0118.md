---
title: "編譯器錯誤 CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0118
'construct1\_name' 是 'construct1'，但卻被當成 'construct2' 使用  
  
 編譯器偵測到建構的使用方式有誤，或在建構上嘗試不允許的作業。 下列為部分範例：  
  
-   嘗試執行個體化命名空間 \(而不是類別\)  
  
-   嘗試呼叫欄位 \(而不是方法\)  
  
-   嘗試將類型作為變數使用  
  
-   嘗試將外部別名作為類型使用。  
  
 若要解決此錯誤，請確認您正在執行的作業對於執行的作業類型來說是有效的。  
  
## 範例  
 下列範例會產生 CS0118：  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```