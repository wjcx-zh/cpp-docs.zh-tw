---
title: "編譯器警告 (層級 3) CS0282 | Microsoft Docs"
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
  - "CS0282"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0282"
ms.assetid: fd4cda5d-81c7-40e3-8424-c938b3447356
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0282
在部分類別或結構 'type' 的多重宣告中，欄位之間沒有已定義的順序。 若要指定順序，所有執行個體欄位必須在同一個宣告中。  
  
 若要解決這個錯誤，請將所有成員變數放在單一部分類別定義中。  
  
 之所以收到這個錯誤，通常是因為在多個位置定義了部分 `struct`，其中一些成員變數在一個定義中，而另一些成員變數在另一個定義中。  
  
 下列程式碼會產生 CS0282。  
  
## 範例  
 這個程式碼包含 `struct` 的一個描述。 請透過下列命令，以單一步驟同時編譯這兩個模組：  
  
 `csc /targt:library cs0282_1.cs cs0282_2.cs`  
  
```  
partial struct A { int i; }  
```  
  
## 範例  
 這個程式碼包含相同 `struct` 的衝突描述。  
  
```  
partial struct A { int j; }  
```