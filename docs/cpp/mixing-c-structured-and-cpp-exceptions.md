---
title: 混合 C （結構化） 和C++例外狀況
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 94d6dc249cb130aaf09d3202b9e8f437d00a9597
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345960"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C （結構化） 和C++例外狀況

如果您想要撰寫可攜式程式碼，使用結構化例外狀況處理 (SEH)C++不在建議程式。 不過，您有時可以使用編譯[/EHa](../build/reference/eh-exception-handling-model.md)混用結構化例外狀況，和C++來源的程式碼，並需要能夠處理這兩種例外狀況。 結構化例外狀況處理常式並沒有物件或類型的例外狀況的概念，因為它無法處理所擲回的例外狀況C++程式碼。 不過， C++ **攔截**處理常式可以處理結構化例外狀況。 C++例外狀況處理語法 (**嘗試**，**擲回**，**攔截**) 不接受 C 編譯器，但結構化例外狀況處理語法 (**__try**， **__except**， **__finally**) 已受到C++編譯器。

請參閱[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)如需如何處理結構化例外狀況當做C++例外狀況。

如果您混用結構化和C++例外狀況，請留意這些潛在的問題：

- C++ 例外狀況和結構化例外狀況無法在同一個函式中混用。

- 終止處理常式 (**__finally**區塊) 一律執行，即使在發生例外狀況之後的回溯。

- C++例外狀況處理可以攔截並保留還原所有編譯的模組中的語意[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項，哪些啟用回溯語意。

- 在某些情況下，可能不會針對所有物件呼叫解構函式的函式。 例如，如果在嘗試透過未初始化的函式指標，呼叫的函式的結構化例外狀況時發生，該函數會採用物件做為參數呼叫前建構，這些物件的解構函式不會呼叫在堆疊回溯。

## <a name="next-steps"></a>後續步驟

- [使用 setjmp 或 longjmp 中的C++程式](../cpp/using-setjmp-longjmp.md)

  在使用上查看更多資訊`setjmp`並`longjmp`在C++程式。

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

  您可以使用之方法的範例請參閱 <<c0>來處理結構化例外狀況。

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
