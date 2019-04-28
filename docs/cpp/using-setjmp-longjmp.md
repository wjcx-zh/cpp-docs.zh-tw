---
title: 使用 setjmp 和 longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 4ead12f79701899b3977993c9de3c3803023150f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364515"
---
# <a name="using-setjmp-and-longjmp"></a>使用 setjmp 和 longjmp

當[setjmp](../c-runtime-library/reference/setjmp.md)並[longjmp](../c-runtime-library/reference/longjmp.md)會一起使用，它們提供方法來執行非區域**goto**。 它們通常用在 C 程式碼來執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫或傳回慣例。

> [!CAUTION]
> 因為`setjmp`並`longjmp`不支援的堆疊框架物件正確解構可能之間C++編譯器，且因為它們可能會阻止區域變數最佳化來會降低效能，我們不建議用於C++程式。 我們建議您改用**嘗試**並**攔截**建構。

如果您決定要使用`setjmp`並`longjmp`在C++程式中，也包含\<setjmp.h > 或\<setjmpex.h > 以確保正確的函式和結構化例外狀況處理 (SEH) 之間的互動或C++例外狀況處理。

**Microsoft 專屬**

如果您使用[/EH](../build/reference/eh-exception-handling-model.md)選項來編譯C++的程式碼，解構函式在堆疊回溯期間呼叫本機物件。 不過，如果您使用 **/EHs**或是 **/EHsc**進行編譯，而會使用您的函式的其中一個[noexcept](../cpp/noexcept-cpp.md)呼叫`longjmp`，則解構函式回溯該函式可能不會發生，根據最佳化工具的狀態。

在可攜式程式碼，當`longjmp`執行呼叫時，畫面格為基礎的物件的正確解構標準，明確地不保證，並不會受到其他編譯器。 若要可讓您知道，在警告層級 4，呼叫`setjmp`會導致警告 C4611: '_setjmp' 之間的互動和C++物件解構是不可移植。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)
