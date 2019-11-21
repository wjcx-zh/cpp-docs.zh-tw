---
title: 'Timing of exception handling: A summary'
ms.date: 05/07/2019
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
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246339"
---
# <a name="timing-of-exception-handling-a-summary"></a>Timing of exception handling: A summary

A termination handler is executed no matter how the **__try** statement block is terminated. Causes include jumping out of the **__try** block, a `longjmp` statement that transfers control out of the block, and unwinding the stack due to exception handling.

> [!NOTE]
>  The Microsoft C++ compiler supports two forms of the `setjmp` and `longjmp` statements. 快速版本會略過終止處理，但是會更有效率。 To use this version, include the file \<setjmp.h>. 另一個版本支援終止處理，如先前段落中所述。 To use this version, include the file \<setjmpex.h>. 快速版本的效能提升取決於硬體組態。

作業系統會先依適當的順序執行所有終止處理常式，型執行其他程式碼，包括例外狀況處理常式的主體。

當導致中斷的原因是來自例外狀況時，系統必須先執行一個或多個例外狀況處理常式的篩選條件部分，再決定要終止哪個部分。 事件的順序為：

1. 引發例外狀況。

1. 系統會查看作用中例外狀況處理常式的階層架構，並執行具有最高優先順序之處理常式的篩選條件，依照區塊和函式呼叫，這會是最近安裝且位於巢狀最深處的例外狀況處理常式。

1. 如果這個篩選條件會傳遞控制權 (傳回 0)，處理序會繼續執行，直到找到不會傳遞控制權的篩選條件。

1. If this filter returns -1, execution continues where the exception was raised, and no termination takes place.

1. 如果篩選條件傳回 1，則會發生下列事件：

   - 系統會回溯堆疊、清除目前執行之程式碼 (即引發例外狀況的位置) 的所有堆疊框架，而包含例外狀況處理常式的堆疊框架會取得控制權。

   - 回溯堆疊時，會執行堆疊上的每個終止處理常式。

   - 例外狀況處理常式本身會執行。

   - 控制權會傳遞給這個例外狀況處理常式結尾後方的程式碼。

## <a name="see-also"></a>請參閱

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)