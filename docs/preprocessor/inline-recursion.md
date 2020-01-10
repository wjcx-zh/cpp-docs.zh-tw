---
title: inline_recursion pragma
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220961"
---
# <a name="inline_recursion-pragma"></a>inline_recursion pragma

控制直接或相互遞迴函式呼叫的內嵌展開。

## <a name="syntax"></a>語法

> **#pragma inline_recursion (** [{ **on**  |  **off** }] **)**

## <a name="remarks"></a>備註

使用此 pragma 控制標記為[inline](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)的函式, 或是編譯器會在`/Ob2`選項下自動展開的函數。 使用此 pragma 時, 必須有1或2的[/Ob](../build/reference/ob-inline-function-expansion.md)編譯器選項設定。 **Inline_recursion**的預設狀態為 off。 這個 pragma 會在出現 pragma 之後, 于第一個函式呼叫中生效, 而且不會影響函數的定義。

**Inline_recursion** pragma 控制遞迴函式的展開方式。 如果**inline_recursion**是 off, 而且內嵌函式直接或間接呼叫本身, 則只會展開一次函數。 如果**inline_recursion**是 on, 函式會展開多次, 直到達到以[inline_depth](../preprocessor/inline-depth.md) pragma 設定的值、 `inline_depth` pragma 所定義之遞迴函式的預設值或容量限制為止。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (內嵌函式展開)](../build/reference/ob-inline-function-expansion.md)
