---
title: 內嵌組譯碼的偵錯和清單
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 6e97c2528f480268599f561e8cf4a1df2518c6b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192180"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>內嵌組譯碼的偵錯和清單

**Microsoft 特定的**

如果您使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項進行編譯，則包含內嵌組解碼程式碼的程式可以使用來源層級偵錯工具進行調試。

在偵錯工具中，您可以在 C 或 C++ 以及組合語言的程式行上設定中斷點。 如果啟用混合組譯碼和來源模式，您可以同時顯示組譯程式碼的原始程式碼和反組譯形式。

請注意，將多個組譯碼指令或來源語言陳述式放在同一程式碼行上，可能會使偵錯的難度提高。 在來源模式下，您可以使用偵錯工具在單一程式行 (而不是在相同程式碼行的個別陳述式上) 上設定中斷點。 相同的原則適用于 **`__asm`** 定義為 C 宏的區塊，它會展開為單一邏輯程式程式碼。

如果您使用[/FAs](../../build/reference/fa-fa-listing-file.md)編譯器選項來建立混合的來源和元件清單，清單中會包含每個組合語言行的來源和元件表單。 巨集不會在清單中展開，但是會在編輯期間展開。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用元件語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
