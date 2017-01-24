---
title: "編譯器錯誤 CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0537
類別 System.Object 不能有基底類別或實作介面  
  
 如果重建 <xref:System> 類別庫，而且 <xref:System.Object> 衍生自另一個類別，則會發生 CS0537。 您不太可能會遇到這個錯誤。 如果您遇到這個錯誤，請不要從類別或介面中衍生 <xref:System.Object>：它是整個 .NET Framework 類別階層的根目錄，因此，不會衍生自其他項目。