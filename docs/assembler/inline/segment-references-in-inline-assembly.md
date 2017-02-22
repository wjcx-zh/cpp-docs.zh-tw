---
title: "內嵌組譯碼中的區段參考 | Microsoft Docs"
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
  - "內嵌組譯碼, 暫存器"
  - "內嵌組譯碼, 區段參考"
  - "參考, 內嵌組譯碼"
  - "暫存器"
  - "暫存器, 內嵌組譯碼"
  - "內嵌組譯碼中的區段參考"
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 內嵌組譯碼中的區段參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 您必須依暫存器參考區段而不是依名稱 \(例如區段名稱 `_TEXT` 無效\)。  區段覆寫必須明確使用暫存器，如 ES:\[BX\]。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)