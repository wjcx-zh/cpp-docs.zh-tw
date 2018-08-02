---
title: 使用 setjmp-longjmp |Microsoft Docs
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
ms.openlocfilehash: 2073729fc5445fc36e3d8a6f52c4f69b079c8b47
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462127"
---
# <a name="using-setjmplongjmp"></a>使用 setjmp/longjmp
當[setjmp](../c-runtime-library/reference/setjmp.md)並[longjmp](../c-runtime-library/reference/longjmp.md)會一起使用，它們提供方法來執行非區域**goto**。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫或傳回慣例。  
  
> [!CAUTION]
>  不過，因為**setjmp**並**longjmp**不支援 c + + 物件語意，而且因為它們可能會阻止區域變數最佳化來會降低效能，我們建議您不要使用它們在 c + + 程式中。 我們建議您改用**嘗試**/**攔截**建構。  
  
 如果您決定要使用**setjmp**/**longjmp**在 c + + 程式中，也包括\<setjmp.h > 或\<setjmpex.h > 以確保正確之間的互動函式和 c + + 例外狀況處理。 如果您使用[/EH](../build/reference/eh-exception-handling-model.md)編譯，堆疊回溯期間呼叫本機物件解構函式。 如果您使用 **/EHs**進行編譯，而其中一個函式呼叫的函式會[nothrow](../cpp/nothrow-cpp.md)使用的函式**nothrow**呼叫**longjmp**，則解構函式回溯可能不會發生，最佳化工具根據。  
  
 在可攜式程式碼，當非區域**goto**它會呼叫**longjmp**執行時，畫面格為基礎的物件的正確解構可能不可靠。  
  
## <a name="see-also"></a>另請參閱  
 [混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)