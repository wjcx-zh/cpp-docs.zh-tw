---
title: __thiscall |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704399"
---
# <a name="thiscall"></a>__thiscall

**Microsoft 專屬**

`__thiscall` 呼叫慣例用於成員函式，而且是不用變數引數的 C++ 成員函式預設的呼叫慣例。 在 `__thiscall` 下，被呼叫端會清除堆疊，而在 `vararg` 函式中這是不可能的。 在 x86 架構，引數從右至左推入至堆疊，其中 `this` 指標透過暫存器 ECX 傳遞，而不是在堆疊上。

使用 `__thiscall` 的一個理由，是在成員函式預設使用 `__clrcall` 的類別中。 在這種情況下，您可以使用 `__thiscall` 讓個別成員函式可從機器碼呼叫。

編譯時[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)，所有函式和函式指標都是`__clrcall`除非另行指定。 **/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

在 Visual c + + 2005年之前的版本`__thiscall`呼叫慣例無法明確地指定在程式中，因為`__thiscall`不是關鍵字。

`vararg` 成員函式使用 `__cdecl` 呼叫慣例。 所有函式引數都推進堆疊中，其中 `this` 指標最後推入堆疊

由於這個呼叫慣例僅適用於 C++，因此沒有 C 名稱裝飾配置。

在 ARM 和 x64 電腦，`__thiscall`會接受並忽略編譯器。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

- [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)
