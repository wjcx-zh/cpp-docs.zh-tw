---
title: 例外狀況處理的時機：摘要
description: 在 Microsoft c + + 中執行例外狀況處理的時間和順序。
ms.date: 08/24/2020
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 2ce501d8d74b6f0f7ca92e193c39f8ce58a66053
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898359"
---
# <a name="timing-of-exception-handling-a-summary"></a>例外狀況處理的時機：摘要

無論語句區塊的結束方式為何，都會執行終止處理常式 **`__try`** 。 原因包括跳過 **`__try`** 區塊、將 `longjmp` 控制權移出區塊的語句，以及因例外狀況處理而回溯堆疊。

> [!NOTE]
> Microsoft c + + 編譯器支援兩種形式的 `setjmp` 和 `longjmp` 語句。 快速版本會略過終止處理，但是會更有效率。 若要使用此版本，請包含檔案 \<setjmp.h> 。 另一個版本支援終止處理，如先前段落中所述。 若要使用此版本，請包含檔案 \<setjmpex.h> 。 快速版本的效能提升取決於硬體組態。

作業系統會先依適當的順序執行所有終止處理常式，型執行其他程式碼，包括例外狀況處理常式的主體。

當導致中斷的原因是來自例外狀況時，系統必須先執行一個或多個例外狀況處理常式的篩選條件部分，再決定要終止哪個部分。 事件的順序為：

1. 引發例外狀況。

1. 系統會查看作用中例外狀況處理常式的階層，並執行具有最高優先順序的處理常式篩選。 這就是最近安裝的例外狀況處理常式，以及最深層的嵌套（由區塊和函式呼叫）。

1. 如果此篩選準則通過控制 (會傳回 0) ，進程會繼續執行，直到找到未通過控制權的篩選準則為止。

1. 如果此篩選傳回-1，則會在引發例外狀況的情況下繼續執行，而且不會進行任何終止。

1. 如果篩選條件傳回 1，則會發生下列事件：

   - 系統回溯堆疊：它會清除引發例外狀況的所有堆疊框架，以及包含例外狀況處理常式的堆疊框架。

   - 回溯堆疊時，會執行堆疊上的每個終止處理常式。

   - 例外狀況處理常式本身會執行。

   - 控制權會傳遞給這個例外狀況處理常式結尾後方的程式碼。

## <a name="see-also"></a>請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
