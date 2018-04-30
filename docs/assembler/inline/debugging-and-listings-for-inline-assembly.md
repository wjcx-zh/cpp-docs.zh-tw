---
title: 偵錯和內嵌組譯碼清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 457402626edcdb2be05923aa33bbd26b1cab7137
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="debugging-and-listings-for-inline-assembly"></a>內嵌組譯碼的偵錯和清單
## <a name="microsoft-specific"></a>Microsoft 特定的  
 包含內嵌組譯碼程式才能進行偵錯使用來源層級偵錯工具如果您使用編譯[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項。  
  
 在偵錯工具中，您可以在 C 或 C++ 以及組合語言的程式行上設定中斷點。 如果啟用混合組譯碼和來源模式，您可以同時顯示組譯程式碼的原始程式碼和反組譯形式。  
  
 請注意，將多個組譯碼指令或來源語言陳述式放在同一程式碼行上，可能會使偵錯的難度提高。 在來源模式下，您可以使用偵錯工具在單一程式行 (而不是在相同程式碼行的個別陳述式上) 上設定中斷點。 相同的原則也適用於定義為 C 巨集 (會將內容展開為單一邏輯程式敘述行) 的 `__asm` 區塊。  
  
 如果您建立混合原始碼和組件列出[/FAs](../../build/reference/fa-fa-listing-file.md)編譯器選項時，清單包含每個組合語言程式行的來源和組件的表單。 巨集不會在清單中展開，但是會在編輯期間展開。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)