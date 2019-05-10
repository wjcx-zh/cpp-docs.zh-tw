---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: e51879ae62b2881e0adadbe59859605f6cc58947
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221906"
---
# <a name="thiscall"></a>__thiscall

**Microsoft 專屬**

**__Thiscall**呼叫慣例用於成員函式，而且是呼叫慣例所使用的預設值C++成員函式不使用變數引數。 底下 **__thiscall**，被呼叫端會清除堆疊，也就是不可能的`vararg`函式。 引數會推送到堆疊上由右至左，與**這**指標傳遞透過暫存器 ECX，而不是在堆疊上的 x86 架構。

若要使用的其中一個原因 **__thiscall**是其成員函式會使用的類別中`__clrcall`預設。 在此情況下，您可以使用 **__thiscall**讓個別成員函式可從原生程式碼呼叫。

進行編譯時[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)，所有函式和函式指標`__clrcall`除非另有指定。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

在 Visual Studio 2005 之前的版本 **__thiscall**呼叫慣例無法明確地指定在程式中，因為 **__thiscall**不是關鍵字。

`vararg` 成員函式會使用 **__cdecl**呼叫慣例。 所有函數引數會都推送到堆疊中，使用**這**指標放置在堆疊上一次

由於這個呼叫慣例僅適用於 C++，因此沒有 C 名稱裝飾配置。

在 ARM 和 x64 機器 **__thiscall**會接受並忽略編譯器。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)