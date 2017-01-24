---
title: "編譯器錯誤 CS1906 | Microsoft Docs"
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
  - "CS1906"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1906"
ms.assetid: 1a6abf5c-f673-4256-93ac-313dce50acc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1906
無效的選項 'option'; 資源可視性必須是 'public' 或 'private'  
  
 此錯誤表示無效的 [\/resource \(將資源檔內嵌至輸出\)](../Topic/-resource%20\(C%23%20Compiler%20Options\).md) 或 [\/linkresource \(連結到 .NET Framework 資源\)](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) 命令列選項。 請檢查 **\/resource** 或 **\/linkresource** 命令列選項的語法，並確定使用的存取範圍修飾詞是 **public** 或 `private`。