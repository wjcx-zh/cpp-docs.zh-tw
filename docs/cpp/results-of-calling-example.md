---
title: 呼叫範例的結果
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 1bf5fe62b8ef2b7a37bf72b7a40e5d47af3f3961
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225874"
---
# <a name="results-of-calling-example"></a>呼叫範例的結果

**Microsoft 特定的**

## <a name="__cdecl"></a>__cdecl

C 裝飾函數名稱是 `_MyFunc` 。

![CDECL 呼叫慣例](../cpp/media/vc37i01.gif "CDECL 呼叫慣例") <br/>
**`__cdecl`** 呼叫慣例

## <a name="__stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 裝飾名稱（ **`__stdcall`** ）為 `_MyFunc@20` 。 C + + 裝飾名稱是實作為特定的。

![&#95;&#95;stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 呼叫慣例") <br/>
__stdcall 和 thiscall 呼叫慣例

## <a name="__fastcall"></a>__fastcall

C 裝飾名稱（ **`__fastcall`** ）為 `@MyFunc@20` 。 C + + 裝飾名稱是實作為特定的。

![ &#95;&#95;fastcall 的呼叫慣例](../cpp/media/vc37i03.gif " &#95;&#95;fastcall 的呼叫慣例") <br/>
__fastcall 呼叫慣例

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)
