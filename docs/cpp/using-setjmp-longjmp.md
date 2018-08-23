---
title: 使用 setjmp 和 longjmp |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: a83253fb98506bb586af2b52ef3321bada7ca01f
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42572048"
---
# <a name="using-setjmp-and-longjmp"></a>使用 setjmp 和 longjmp

當[setjmp](../c-runtime-library/reference/setjmp.md)並[longjmp](../c-runtime-library/reference/longjmp.md)會一起使用，它們提供方法來執行非區域**goto**。 它們通常用在 C 程式碼來執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫或傳回慣例。

> [!CAUTION]
> 因為`setjmp`和`longjmp`不支援正確解構可能之間 c + + 編譯器的堆疊框架物件，因為它們可能會阻止區域變數最佳化來會降低效能，我們不建議用於 c + +程式。 我們建議您改用**嘗試**並**攔截**建構。

如果您決定要使用`setjmp`並`longjmp`在 c + + 程式中，也包括\<setjmp.h > 或\<setjmpex.h > 以確保正確互動之間的函式和結構化例外狀況處理 (SEH) 或 c + + 例外狀況處理方式。

**Microsoft 專屬**

如果您使用[/EH](../build/reference/eh-exception-handling-model.md)選項編譯 c + + 程式碼時，堆疊回溯期間呼叫本機物件的解構函式。 不過，如果您使用 **/EHs**或是 **/EHsc**進行編譯，而會使用您的函式的其中一個[noexcept](../cpp/noexcept-cpp.md)呼叫`longjmp`，則解構函式回溯該函式可能不會發生，根據最佳化工具的狀態。

在可攜式程式碼，當`longjmp`執行呼叫時，畫面格為基礎的物件的正確解構標準，明確地不保證，並不會受到其他編譯器。 若要可讓您知道，在警告層級 4，呼叫`setjmp`會導致警告 C4611: '_setjmp' 和 c + + 物件解構間的互動是不可移植。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
