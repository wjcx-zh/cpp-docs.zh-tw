---
title: inline_recursion |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c22a9fa20e663a87d10dcb1e9ba154c921a5bf8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391302"
---
# <a name="inlinerecursion"></a>inline_recursion
控制直接或相互遞迴函式呼叫的內嵌展開。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>備註  
 
使用這個 pragma 可控制函式標示為[內嵌](../cpp/inline-functions-cpp.md)並[__inline](../cpp/inline-functions-cpp.md)或 函式，編譯器會自動展開下`/Ob2`選項。 需要使用這個 pragma [/Ob](../build/reference/ob-inline-function-expansion.md)編譯器選項設定為 1 或 2。 預設狀態**inline_recursion**已關閉。 這個 pragma 會在 pragma 出現後的第一個函式呼叫中生效，而且不會影響該函式的定義。  
  
**Inline_recursion** pragma 控制遞迴函式展開的方式。 如果**inline_recursion**已關閉，而且如果內嵌函式呼叫本身 （直接或間接），函式展開只會一次。 如果**inline_recursion**已開啟，直到達到設定的值，此函式會展開多次[inline_depth](../preprocessor/inline-depth.md) pragma，遞迴函式的預設值所定義`inline_depth` pragma 或容量限制。  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob (內嵌函式展開)](../build/reference/ob-inline-function-expansion.md)