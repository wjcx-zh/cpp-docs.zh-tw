---
title: 終止處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 6c39407270037756c55dc42aed80e1d04616c9ee
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246374"
---
# <a name="restrictions-on-termination-handlers"></a>終止處理常式的限制

You cannot use a **goto** statement to jump into a **__try** statement block or a **__finally** statement block. 您必須改為透過一般控制流程進入陳述式區塊。 (You can, however, jump out of a **__try** statement block.) Also, you cannot nest an exception handler or termination handler inside a **__finally** block.

此外，終止處理常式中允許的某些類型程式碼會產生可疑的結果，因此使用這類程式碼時應特別小心 (如果一定要的話)。 One is a **goto** statement that jumps out of a **__finally** statement block. 如果區塊在正常終止的過程中執行，則不會發生異常狀況。 但是，如果系統回溯堆疊，則該回溯會停止，而且目前函式會取得控制項，就如同從未發生異常終止一般。

A **return** statement inside a **__finally** statement block presents roughly the same situation. 控制項會返回包含終止處理常式之函式的立即呼叫者。 如果系統回溯堆疊，這個處理序就會停止，而且程式會繼續執行，就如同從未引發例外狀況一般。

## <a name="see-also"></a>請參閱

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)