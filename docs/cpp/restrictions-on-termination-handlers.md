---
title: 終止處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179064"
---
# <a name="restrictions-on-termination-handlers"></a>終止處理常式的限制

您不能使用**goto**語句跳到 **__try**語句區塊或 **__finally**的語句區塊中。 您必須改為透過一般控制流程進入陳述式區塊。 （不過，您可以跳到 **__try**語句區塊）。此外，您無法將例外狀況處理常式或終止處理常式嵌入 **__finally**區塊內。

此外，終止處理常式中允許的某些類型程式碼會產生可疑的結果，因此使用這類程式碼時應特別小心 (如果一定要的話)。 其中一個是**goto**語句，會跳出 **__finally**語句區塊。 如果區塊在正常終止的過程中執行，則不會發生異常狀況。 但是，如果系統回溯堆疊，則該回溯會停止，而且目前函式會取得控制項，就如同從未發生異常終止一般。

在 **__finally**語句區塊內的**return**語句，大致呈現相同的情況。 控制項會返回包含終止處理常式之函式的立即呼叫者。 如果系統回溯堆疊，這個處理序就會停止，而且程式會繼續執行，就如同從未引發例外狀況一般。

## <a name="see-also"></a>另請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
