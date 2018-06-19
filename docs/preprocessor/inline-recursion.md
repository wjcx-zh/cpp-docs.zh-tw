---
title: inline_recursion |Microsoft 文件
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
ms.openlocfilehash: f81347c8286dfa1f0651af43bd3134565a22aade
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849492"
---
# <a name="inlinerecursion"></a>inline_recursion
控制直接或相互遞迴函式呼叫的內嵌展開。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>備註  
 使用這個 pragma 控制函式標示為[內嵌](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)或編譯器會自動在 /Ob2 選項底下展開的函式。 使用這個 pragma 必須[須遵循 /Ob](../build/reference/ob-inline-function-expansion.md)編譯器選項設定為 1 或 2。 `inline_recursion` 的預設狀態是關閉的。 這個 pragma 會在 pragma 出現後的第一個函式呼叫中生效，而且不會影響該函式的定義。  
  
 `inline_recursion` pragma 控制遞迴函式的展開方式。 如果 `inline_recursion` 已關閉，且內嵌函式呼叫其本身 (直接或間接)，則該函式只會展開一次。 如果`inline_recursion`函式會展開多次，直到達到設定的值為 on， [inline_depth](../preprocessor/inline-depth.md) pragma，遞迴函式所定義的預設值`inline_depth`pragma 或容量限制.  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_depth](../preprocessor/inline-depth.md)   
 [/Ob (內嵌函式展開)](../build/reference/ob-inline-function-expansion.md)