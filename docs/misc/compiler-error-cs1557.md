---
title: "編譯器錯誤 CS1557 | Microsoft Docs"
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
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1557
Main 方法無法使用 'class'，因為兩者在不同的輸出檔中  
  
 在多重輸出檔編譯中，針對一個輸出檔指定了 [\/main](../Topic/-main%20\(C%23%20Compiler%20Options\).md) 編譯器選項。 不過，在原始程式碼中找不到此類別可進行 \/main 碼編譯; 在編譯中之其他輸出檔之一的原始程式碼檔案中找到它。