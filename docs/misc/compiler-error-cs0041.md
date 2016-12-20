---
title: "編譯器錯誤 CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0041
偵錯資訊的 'type' 完整名稱太長。 不使用 '\/debug' 選項進行編譯。  
  
 使用 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 編譯器選項時，會發生此錯誤。 如果您遇到這個錯誤，請嘗試刪除 bin 目錄中的 PDB 檔案，並重新編譯。 如果您仍然遇到這個錯誤，可能必須修復或重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。