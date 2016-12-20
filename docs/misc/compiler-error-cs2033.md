---
title: "編譯器錯誤 CS2033 | Microsoft Docs"
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
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2033
無法建立短檔名 'filename'，因為已經有個長檔名具有相同的短檔名  
  
 編譯名稱超過八個字元的任何 C\# 檔案。 然後編譯另一個檔案，使用先前檔案名稱的簡短版本，例如名稱的前六個字元加上 "~1"。 第二次編譯會產生此錯誤。  
  
 若要解決此錯誤，請將短檔名重新命名為不與長檔名衝突的名稱。