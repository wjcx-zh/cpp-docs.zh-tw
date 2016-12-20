---
title: "特性指引最佳化錯誤 PG0165 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PG0165"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PG0165"
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 特性指引最佳化錯誤 PG0165
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

正在讀取 'Filename.pgd' : '不支援的 PGD 版本 \(版本不符\)'。  
  
 PGD 檔案是特定編譯器 \(Compiler\) 工具組專有的檔案。  當您使用的編譯器與 *Filename*.pgd 的不同，就會產生這個錯誤。  這個錯誤表示這個編譯器工具組無法使用 *Filename*.pgd 的資料來最佳化目前的程式。  
  
 若要解決此問題，請使用目前的編譯器工具組重新產生 *Filename*.pgd。