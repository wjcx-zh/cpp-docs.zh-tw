---
title: "內嵌組譯碼的偵錯和清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 偵錯"
  - "錯誤, __asm 區塊"
  - "偵錯 [C++], 內嵌組譯程式碼"
  - "內嵌組譯碼, 偵錯"
  - "內嵌組譯碼, 清單"
  - "來源層級偵錯工具"
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 內嵌組譯碼的偵錯和清單
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 如果您以 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 選項進行編譯，則可以使用來源層級偵錯工具對包含內嵌組譯程式碼的程式進行偵錯。  
  
 在偵錯工具中，您可以在 C 或 C\+\+ 以及組合語言的程式行上設定中斷點。  如果啟用混合組譯碼和來源模式，您可以同時顯示組譯程式碼的原始程式碼和反組譯形式。  
  
 請注意，將多個組譯碼指令或來源語言陳述式放在同一程式碼行上，可能會使偵錯的難度提高。  在來源模式下，您可以使用偵錯工具在單一程式行 \(而不是在相同程式碼行的個別陳述式上\) 上設定中斷點。  相同的原則也適用於定義為 C 巨集 \(會將內容展開為單一邏輯程式敘述行\) 的 `__asm` 區塊。  
  
 如果您使用 [\/FAs](../../build/reference/fa-fa-listing-file.md) 編譯器選項建立混合原始碼和組譯碼的清單，此清單會內含每個組合語言程式行的原始碼和組譯碼形式。  巨集不會在清單中展開，但是會在編輯期間展開。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)