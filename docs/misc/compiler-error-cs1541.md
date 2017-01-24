---
title: "編譯器錯誤 CS1541 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1541
無效的參考選項：'symbol' \-\- 不能參考目錄  
  
 編譯器偵測到嘗試指定目錄，而不是特定檔案。 例如，當您使用 [\/reference](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) 編譯器選項時，必須指定檔案，而不能指定目錄。  
  
 例如，將 `/reference:c:\` 傳遞給編譯器會產生 CS1541。