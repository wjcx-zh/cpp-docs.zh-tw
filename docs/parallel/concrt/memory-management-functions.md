---
title: 記憶體管理函式
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: 9a7810267c3eaa11ad7592774440365620e7e8f4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276932"
---
# <a name="memory-management-functions"></a>記憶體管理函式

本文件說明並行執行階段提供可協助您配置和釋放記憶體，以並行方式記憶體管理函式。

> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。

並行執行階段提供兩種記憶體管理函式，最適合用於配置及釋放記憶體區塊，以並行方式。 [Concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)函式會使用指定的大小來配置記憶體區塊。 [Concurrency:: free](reference/concurrency-namespace-functions.md#free)函式會釋放已配置的記憶體`Alloc`。

> [!NOTE]
>  `Alloc`和`Free`函式互相依賴。 使用`Free`函式只能用來釋放您配置使用的記憶體`Alloc`函式。 此外，當您使用`Alloc`函式以配置記憶體，請只使用`Free`函式來釋放該記憶體。

使用`Alloc`和`Free`函式，當您配置和釋放一組固定的配置大小，從不同的執行緒或工作。 並行執行階段會快取它從 C 執行階段堆積中配置的記憶體。 並行執行階段會保留每個執行中的執行緒; 不同的記憶體快取因此，執行階段會管理記憶體，而不使用鎖定或記憶體屏障。 應用程式有益於更`Alloc`和`Free`函式時較常存取的記憶體快取。 比方說，經常呼叫的執行緒`Alloc`並`Free`主要呼叫執行緒以外的更多的優勢`Alloc`或`Free`。

> [!NOTE]
>  當您使用這些記憶體管理函式中，而且可能需要輸入您的應用程式會使用大量記憶體，應用程式記憶體不足的狀況更快比您預期。 因為會由一個執行緒快取的記憶體區塊並不適用於任何其他執行緒，如果一個執行緒保存大量的記憶體，所以無法使用記憶體。

## <a name="example"></a>範例

如需使用的範例`Alloc`並`Free`函式來改善記憶體效能，請參閱[How to:使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
