---
title: 混合 C （結構化） 和 c + + 例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1edd35ac9f32a28a19c4ea54b7e9fba2820d6095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031622"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C （結構化） 和 c + + 例外狀況

如果您想要撰寫可攜式程式碼，不建議使用 c + + 程式中處理 (SEH) 的結構化例外狀況。 不過，您有時可以使用編譯[/EHa](../build/reference/eh-exception-handling-model.md)混用結構化例外狀況和 c + + 原始程式碼，並需要能夠處理這兩種例外狀況。 結構化例外狀況處理常式並沒有物件或類型的例外狀況的概念，因為它無法處理 c + + 程式碼擲回的例外狀況。 不過，c + +**攔截**處理常式可以處理結構化例外狀況。 C + + 例外狀況處理語法 (**嘗試**，**擲回**，**攔截**) 不接受 C 編譯器，但結構化例外狀況處理語法 (**__try**， **__except**， **__finally**) 支援 c + + 編譯器。

請參閱[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)如需有關如何處理結構化例外狀況當做 c + + 例外狀況資訊。

如果您混用結構化和 c + + 例外狀況，請留意這些潛在的問題：

- C++ 例外狀況和結構化例外狀況無法在同一個函式中混用。

- 終止處理常式 (**__finally**區塊) 一律執行，即使在發生例外狀況之後的回溯。

- C + + 例外狀況處理可以攔截並保留還原所有編譯的模組中的語意[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項，哪些啟用回溯語意。

- 在某些情況下，可能不會針對所有物件呼叫解構函式的函式。 例如，如果在嘗試透過未初始化的函式指標，呼叫的函式的結構化例外狀況時發生，該函數會採用物件做為參數呼叫前建構，這些物件的解構函式不會呼叫在堆疊回溯。

## <a name="next-steps"></a>後續步驟

- [在 c + + 程式中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)

  在使用上查看更多資訊`setjmp`和`longjmp`c + + 程式中。

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

  請參閱您可以使用 c + + 來處理結構化例外狀況之方法的範例。

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
