---
title: "呼叫範例的結果 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eaa47af17e46f51ef92cc15b8d2275b2ed8e05f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="results-of-calling-example"></a>呼叫範例的結果
## <a name="microsoft-specific"></a>Microsoft 特定的  
  
## <a name="cdecl"></a>__cdecl  
 C 裝飾函式名稱為 "_MyFunc"。  
  
 ![CDECL 呼叫慣例](../cpp/media/vc37i01.gif "vc37I01")  
__cdecl 呼叫慣例  
  
## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall  
 C 裝飾名稱 (`__stdcall`) 是 「_MyFunc@20。 」 C++ 裝飾名稱為機密。  
  
 ![&#95; &#95; stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.gif "vc37I02")  
__stdcall 和 thiscall 呼叫慣例  
  
## <a name="fastcall"></a>__fastcall  
 C 裝飾名稱 (`__fastcall`) 是 「@MyFunc@20。 」 C++ 裝飾名稱為機密。  
  
 ![呼叫慣例 &#95; &#95; fastcall](../cpp/media/vc37i03.gif "vc37I03")  
__fastcall 呼叫慣例  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)