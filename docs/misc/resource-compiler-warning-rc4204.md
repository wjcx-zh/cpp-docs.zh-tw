---
title: "資源編譯器警告 RC4204 | Microsoft Docs"
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
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 資源編譯器警告 RC4204
ASCII 字元不等同虛擬按鍵碼  
  
 針對 VIRTKEY 類型快速鍵中的虛擬按鍵碼使用了字串常值。  
  
 這則警告允許您繼續進行；但請注意，所產生的快速鍵可能不符合您指定的字串 \(VIRTKEY 使用不同於 ASCII 快速鍵的按鍵碼\)。  
  
 雖然字串常值的語法有效，但唯有在 WINDOWS.h 中使用 **VK\_\***`#define` 值，才能確保取得所需的快速鍵。