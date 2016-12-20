---
title: "編譯器警告 (層級 2) CS0444 | Microsoft Docs"
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
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0444
'System namespace 1' 中找不到預先定義的類型 'type name 1'，卻在 'System namespace 2' 中找到  
  
 預先定義的物件，例如 <xref:System.Int32>，在編譯器應該找到的位置找不到，卻在 'System namespace 2' 中找到。  
  
 此錯誤可能表示 .NET Framework 安裝不正確。 若要修正這個問題，請重新安裝 .NET Framework。  
  
 如果您在撰寫自己的基底類別程式庫，可能也會發生這個錯誤。 發生這種狀況時，若要解決問題，請重建 mscorlib。