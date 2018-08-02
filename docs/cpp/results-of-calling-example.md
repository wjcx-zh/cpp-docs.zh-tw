---
title: 呼叫範例的結果 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c49457aecb93b16ffb294f88e4f6643826492e2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465687"
---
# <a name="results-of-calling-example"></a>呼叫範例的結果
## <a name="microsoft-specific"></a>Microsoft 特定的  
  
## <a name="cdecl"></a>__cdecl  
 C 裝飾函式名稱為 "_MyFunc"。  
  
 ![CDECL 呼叫慣例](../cpp/media/vc37i01.gif "vc37I01")  
**__Cdecl**呼叫慣例  
  
## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall  
 C 裝飾名稱 (**__stdcall**) 是 「_MyFunc@20。 」 C++ 裝飾名稱為機密。  
  
 ![&#95;&#95;stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.gif "vc37I02")  
__stdcall 和 thiscall 呼叫慣例  
  
## <a name="fastcall"></a>__fastcall  
 C 裝飾名稱 (**__fastcall**) 是 「@MyFunc@20。 」 C++ 裝飾名稱為機密。  
  
 ![呼叫慣例，如&#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
__fastcall 呼叫慣例  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)