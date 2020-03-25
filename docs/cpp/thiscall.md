---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188151"
---
# <a name="__thiscall"></a>__thiscall

**Microsoft 專屬**

**__Thiscall**呼叫慣例是在成員函式上使用，而且是不使用變數自C++變數的成員函式所使用的預設呼叫慣例。 在 **__thiscall**下，被呼叫端會清除堆疊，這對 `vararg` 函式而言是不可能的。 引數會從右至左推送至堆疊，而**此**指標會透過暫存器 ECX 傳遞，而不是在堆疊上，透過 x86 架構。

使用 **__thiscall**的其中一個原因是在預設的成員函式使用 `__clrcall` 的類別中。 在這種情況下，您可以使用 **__thiscall** ，讓個別成員函式可從機器碼呼叫。

以[/clr： pure](../build/reference/clr-common-language-runtime-compilation.md)進行編譯時，除非另有指定，否則會 `__clrcall` 所有函式和函式指標。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

在 Visual Studio 2005 之前的版本中，無法在程式中明確指定 **__thiscall**呼叫慣例，因為 **__thiscall**不是關鍵字。

`vararg` 成員函式會使用 **__cdecl**呼叫慣例。 所有函式引數會推送至堆疊上，最後放在堆疊上的**this**指標

由於這個呼叫慣例僅適用於 C++，因此沒有 C 名稱裝飾配置。

在 ARM 和 x64 電腦上，編譯器會接受並忽略 **__thiscall** 。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)
