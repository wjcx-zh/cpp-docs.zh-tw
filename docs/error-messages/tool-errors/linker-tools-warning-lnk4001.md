---
title: "連結器工具警告 LNK4001 | Microsoft Docs"
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
  - "LNK4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4001"
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未指定物件檔；已忽略程式庫  
  
 已傳送一或多個 .lib 檔案至連結器，但是沒有傳送 .obj 檔案。  
  
 因為連結器無法存取 .lib 檔案的資訊，但是可以存取 .obj 檔案的資訊，所以此警告指出您必須明確指定其他的連結器選項。  例如，您可能必須指定 [\/MACHINE](../../build/reference/machine-specify-target-platform.md)、[\/OUT](../../build/reference/out-output-file-name.md) 或 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 選項。