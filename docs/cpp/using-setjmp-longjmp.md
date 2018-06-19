---
title: 使用 setjmp longjmp |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dee79d5b81e968e89e8072fb545c86f33be9bcce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422601"
---
# <a name="using-setjmplongjmp"></a>使用 setjmp/longjmp
當[setjmp](../c-runtime-library/reference/setjmp.md)和[longjmp](../c-runtime-library/reference/longjmp.md)會一起使用，提供的方式來執行非區域`goto`。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫或傳回慣例。  
  
> [!CAUTION]
>  不過，由於 `setjmp` 和 `longjmp` 不支援 C++ 物件語意，而且它們可能會阻止區域變數最佳化而造成效能降低，因此建議您不要在 C++ 程式中使用它們。 我們建議您改用`try` / `catch`建構。  
  
 如果您決定使用`setjmp` / `longjmp`在 c + + 程式中，也包括\<setjmp.h > 或\<setjmpex.h > 若要確保正確函式和 c + + 例外狀況處理之間的互動。 如果您使用[/EH](../build/reference/eh-exception-handling-model.md)進行編譯時，堆疊回溯期間呼叫本機物件解構函式。 如果您使用 **/EHs**進行編譯，而其中一個函式呼叫的函式，使用[nothrow](../cpp/nothrow-cpp.md)使用的函式`nothrow`呼叫`longjmp`，則解構函式回溯可能不會發生，根據最佳化工具。  
  
 在可攜式程式碼中，當執行呼叫 `goto` 的非本機 `longjmp` 時，畫面物件的正確解構可能不可靠。  
  
## <a name="see-also"></a>另請參閱  
 [混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)