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
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268034"
---
# <a name="results-of-calling-example"></a>呼叫範例的結果

**Microsoft 專屬**

## <a name="cdecl"></a>__cdecl

C 裝飾函式名稱`_MyFunc`。

![CDECL 呼叫慣例](../cpp/media/vc37i01.gif "CDECL 呼叫慣例") <br/>
**__Cdecl**呼叫慣例

## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 裝飾名稱 (**__stdcall**) 是`_MyFunc@20`。 C++是實作專用的裝飾的名稱。

![&#95;&#95;stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 呼叫慣例") <br/>
__stdcall 和 thiscall 呼叫慣例

## <a name="fastcall"></a>__fastcall

C 裝飾名稱 (**__fastcall**) 是`@MyFunc@20`。 C++是實作專用的裝飾的名稱。

![呼叫慣例，如&#95; &#95;fastcall](../cpp/media/vc37i03.gif "呼叫慣例的&#95; &#95;fastcall") <br/>
__fastcall 呼叫慣例

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)