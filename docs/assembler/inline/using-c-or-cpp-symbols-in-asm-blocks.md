---
title: 在 __asm 區塊中使用 C 或 c + + 符號 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ba8426e2a7ae1152a41fafa0c239498801c6e4d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678889"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>在 __asm 區塊中使用 C 或 C++ 符號

**Microsoft 專屬**

一個 `__asm` 區塊可以在出現區塊的範圍中參考任何 C 或 C++ 符號。 (C 和 C++ 符號為變數名稱、函式名稱和標籤，亦即不是符號常數或 `enum` 成員的名稱。 您不能呼叫 C++ 成員函式)。

使用 C 和 C++ 符號時有一些限制：

- 每個組合語言陳述式只能包含一個 C 或 C++ 符號。 多個符號可以出現在相同的組譯碼指令，只能搭配**長度**，**型別**，並**大小**運算式。

- 在程式的前方必須宣告 (原型) `__asm` 區塊參考的函式。 否則，編譯器無法區分 `__asm` 區塊中的函式名稱和標籤。

- `__asm` 區塊不能使用任何與 MASM 保留字 (不區分大小寫) 相同拼字的 C 或 C++ 符號。 MASM 保留字包括指令名稱這類**推播**並註冊名稱，例如 SI。

- 在 `__asm` 區塊中無法辨識結構和等位標記。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>