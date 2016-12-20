---
title: "編譯器錯誤 CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0250
不要直接呼叫您的基底類別 Finalize 方法。 會從您的解構函式自動呼叫它。  
  
 程式無法嘗試強制清除基底類別資源。  
  
 如需詳細資訊，請參閱[Finalize 方法和解構函式](http://msdn.microsoft.com/zh-tw/fd376774-1643-499b-869e-9546a3aeea70)。  
  
 下列範例會產生 CS0250：  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```