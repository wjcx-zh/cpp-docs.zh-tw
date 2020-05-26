---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854810"
---
# `__thiscall`

**Microsoft 特定**的 **`__thiscall`** 呼叫慣例是在 x86 架構上的 c + + 類別成員函式上使用。 這是不使用變數引數（函式）的成員函式所使用的預設呼叫慣例 `vararg` 。

在下 **`__thiscall`** ，被呼叫端會清除堆疊，這對函式而言是不可能的 `vararg` 。 引數會從右至左推送至堆疊。 指標透過暫存器 **`this`** ECX 傳遞，而不是在堆疊上。

在 ARM、ARM64 和 x64 電腦上， **`__thiscall`** 編譯器會接受並忽略。 這是因為根據預設，它們會使用以註冊為基礎的呼叫慣例。

其中一個使用的原因 **`__thiscall`** 是，其成員函式預設使用的類別 **`__clrcall`** 。 在此情況下，您可以使用 **`__thiscall`** 讓個別成員函式可從機器碼呼叫。

使用進行編譯時 [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) ，除非另有指定，否則所有函式和函式指標都是 **`__clrcall`** 。 **`/clr:pure`** 和 **`/clr:safe`** 編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

`vararg`成員函式使用 **`__cdecl`** 呼叫慣例。 所有函式引數會推送至堆疊上，並將 **`this`** 指標最後放在堆疊上。

因為此呼叫慣例僅適用于 c + +，所以它沒有 C 名稱裝飾配置。

當您定義非靜態類別成員函式時，請只在宣告中指定呼叫慣例修飾詞。 您不需要在非正規定義上再次指定它。 編譯器會在定義時使用在宣告期間指定的呼叫慣例。

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)
