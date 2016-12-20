---
title: "編譯器錯誤 CS1509 | Microsoft Docs"
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
  - "CS1509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1509"
ms.assetid: 51a475c3-f085-49cb-89b0-c6582b68653f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1509
所參考的檔案 'file' 不是組件; 請使用 '\/addmodule' 選項替代  
  
 在編譯中產生的輸出檔 \(輸出檔 1\)，且它使用 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) \(沒有組件資訊清單\)，已指定給 [\/reference](../Topic/-reference%20\(C%23%20Compiler%20Options\).md)。 所以，輸出檔 1 內的中繼資料資訊將會加入目前程式的組件，而不是將組件附加至目前程式的組件。