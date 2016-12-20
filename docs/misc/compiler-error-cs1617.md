---
title: "編譯器錯誤 CS1617 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1617
無效的 \/langversion 選項 'option'; 必須是 ISO\-1、ISO\-2 或 Default  
  
 如果您使用 [\/langversion](../Topic/-langversion%20\(C%23%20Compiler%20Options\).md) 命令列參數或專案設定，但未指定有效的語言選項，就會發生這個錯誤。 若要解決這個錯誤，請檢查命令列語法或專案設定，並將其變更為其中一個列出的選項。  
  
 例如，以 `csc /langversion:ISO` 編譯會產生錯誤 CS1617。