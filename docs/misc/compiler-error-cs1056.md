---
title: "編譯器錯誤 CS1056 | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1056"
ms.assetid: bf66d164-ab5b-4181-b93e-a1d29620b4d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1056
不應該有字元 'character'  
  
 C\# 編譯器遇到未預期的字元，而且無法識別目前正在處理的語彙基元。 例如，如果編譯器在處理識別項期間遇到歐元字元，將無法分類識別項，因為歐元字元只在字串中有效，而且編譯器知道它不是處理字串。