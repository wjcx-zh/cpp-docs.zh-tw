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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179051"
---
# <a name="results-of-calling-example"></a>呼叫範例的結果

**Microsoft 專屬**

## <a name="__cdecl"></a>__cdecl

`_MyFunc`C 裝飾函數名稱。

![CDECL 呼叫慣例](../cpp/media/vc37i01.gif "CDECL 呼叫慣例") <br/>
**__Cdecl**呼叫慣例

## <a name="__stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 裝飾名稱（ **__stdcall**）是 `_MyFunc@20`。 C++裝飾名稱是實作為特定。

![&#95;&#95;stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 呼叫慣例") <br/>
__stdcall 和 thiscall 呼叫慣例

## <a name="__fastcall"></a>__fastcall

C 裝飾名稱（ **__fastcall**）是 `@MyFunc@20`。 C++裝飾名稱是實作為特定。

![Fastcall 的&#95; &#95;呼叫慣例](../cpp/media/vc37i03.gif "Fastcall 的&#95; &#95;呼叫慣例") <br/>
__fastcall 呼叫慣例

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)
