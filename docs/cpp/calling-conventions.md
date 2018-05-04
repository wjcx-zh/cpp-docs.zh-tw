---
title: 呼叫慣例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9e65dfd7f7cff25debd8eb0d00a7e3bb0397692
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="calling-conventions"></a>呼叫慣例
Visual C/C++ 編譯器提供數個用於呼叫內部和外部函式的不同慣例。 了解這些不同的方法可協助您偵錯程式，並將您的程式碼與組合語言常式連結。  
  
 與此主旨有關的主題將說明呼叫慣例之間的差異、引數傳遞方式，以及函式傳回值的方式。 並且也會探討 naked 函式呼叫，這是一個讓您自行撰寫初構和終解程式碼的進階功能。  
  
 如需有關適用於 x64 呼叫慣例詳細的處理器，請參閱[呼叫慣例](../build/calling-convention.md)。  
  
## <a name="topics-in-this-section"></a>本節主題  
  
-   [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)(`__cdecl`， `__stdcall`， `__fastcall`，等等)  
  
-   [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [使用 naked 函式呼叫撰寫自訂初構/終解程式碼](../cpp/naked-function-calls.md)  
  
-   [浮點常數副處理器和呼叫慣例](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [過時呼叫慣例](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)