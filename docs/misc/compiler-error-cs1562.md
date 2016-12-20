---
title: "編譯器錯誤 CS1562 | Microsoft Docs"
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
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1562
沒有來源的輸出必須有指定的 \/out 選項  
  
 此編譯可建立輸出檔，但沒有作為輸入的原始程式碼檔，以從中隱含輸出檔的名稱。 例如，您可能嘗試編譯中繼資料或資源專用檔。  
  
 請使用 [\/out](../Topic/-out%20\(C%23%20Compiler%20Options\).md) 編譯器選項以指定輸出檔的名稱。