---
title: 終止處理常式的限制
description: 結構化例外狀況處理終止處理常式的限制。
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 60fdb4c2a105f2fce4a32f475563a04f8e7bfaf9
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898267"
---
# <a name="restrictions-on-termination-handlers"></a>終止處理常式的限制

您無法使用 **`goto`** 語句跳到 **`__try`** 語句區塊或 **`__finally`** 語句區塊。 您必須改為透過一般控制流程進入陳述式區塊。 不過 (您可以跳出 **`__try`** 語句區塊 ) 。此外，您也無法在區塊內將例外狀況處理常式或終止處理常式嵌入。 **`__finally`**

終止處理常式中允許的一些程式碼會產生可疑的結果，因此您應該謹慎使用它們。 其中一個是 **`goto`** 跳出語句區塊的語句 **`__finally`** 。 如果在正常終止的過程中執行區塊，就不會發生任何異常狀況。 但是，如果系統回溯堆疊，就會停止。 然後，目前的函式會取得控制項，如同沒有異常終止。

**`return`** 語句區塊內的語句大致上有 **`__finally`** 相同的情況。 控制權會返回包含終止處理常式之函式的立即呼叫端。 如果系統回溯堆疊，就會停止此進程。 然後，程式會繼續執行，就像未引發任何例外狀況一樣。

## <a name="see-also"></a>請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
