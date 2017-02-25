---
title: "嚴重錯誤 C1067 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1067"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1067"
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 嚴重錯誤 C1067
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制 : 已超過型別記錄的 64K 大小限制  
  
 符號具有超過 247 個字元的裝飾名稱 \(Decorated Name\) 時，可能會發生這種錯誤。若要解決這個問題，請縮短符號名稱。  
  
 當編譯器產生偵錯資訊時，它會發出型別記錄，以定義原始程式碼中所遭遇到的型別。例如，型別記錄包含簡單的結構和函式的引數清單。有些型別記錄可能會是大型清單。  
  
 任何型別記錄都會有 64K 的大小限制。如果超過 64K 限制，就會發生錯誤。  
  
 如果有許多長名稱的符號，或是類別、結構或等位的成員太多，都可能會發生 C1067。