---
title: "最佳化內嵌組譯碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 最佳化"
  - "內嵌組譯碼, 最佳化"
  - "最佳化, 內嵌組譯碼"
  - "最佳化效能, 內嵌組譯碼"
  - "儲存體, 在內嵌組譯碼中最佳化"
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 最佳化內嵌組譯碼
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 函式中若存在 `__asm` 區塊，則會透過多種方式影響最佳化。  首先，編譯器不會嘗試最佳化 `__asm` 區塊本身。  您在組合語言中撰寫的內容即會與取得的內容完全相同。  其次，`__asm` 區塊會影響暫存器變數儲存區。  如果 `__asm` 區塊可能會變更暫存器的內容，則編譯器會避免跨 `__asm` 區塊註冊這些變數。  最後，其他函式最佳化會受到函式中包含的組合語言所影響。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)