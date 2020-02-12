---
title: 記憶體管理函式
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141833"
---
# <a name="memory-management-functions"></a>記憶體管理函式

本檔說明並行執行階段所提供的記憶體管理功能，以協助您以並行方式配置和釋放記憶體。

> [!TIP]
> 並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，因此如果您不熟悉並行執行階段，建議您從[平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫開始。

並行執行階段提供兩個記憶體管理功能，最適合用來以並行方式配置和釋放記憶體區塊。 [Concurrency：：](reference/concurrency-namespace-functions.md#alloc)配置函數會使用指定的大小來配置記憶體區塊。 [Concurrency：： Free](reference/concurrency-namespace-functions.md#free)函式會釋出 `Alloc`所配置的記憶體。

> [!NOTE]
> `Alloc` 和 `Free` 函數會彼此依賴。 僅使用 `Free` 函式釋放您使用 `Alloc` 函數配置的記憶體。 此外，當您使用 `Alloc` 函式來配置記憶體時，請只使用 `Free` 函數釋放該記憶體。

當您從不同的執行緒或工作配置和釋放一組固定的配置大小時，請使用 `Alloc` 和 `Free` 函式。 並行執行階段會快取它從 C 執行時間堆積配置的記憶體。 並行執行階段會針對每個執行中的執行緒保存個別的記憶體快取;因此，執行時間會管理記憶體，而不會使用鎖定或記憶體屏障。 當更頻繁地存取記憶體快取時，應用程式從 `Alloc` 和 `Free` 函式受益。 例如，經常呼叫 `Alloc` 和 `Free` 優點的執行緒，會比主要呼叫 `Alloc` 或 `Free`的執行緒還多。

> [!NOTE]
> 當您使用這些記憶體管理函式，而且您的應用程式使用大量的記憶體時，應用程式可能會比預期更快進入記憶體不足的狀況。 由於某個執行緒快取的記憶體區塊無法供任何其他執行緒使用，因此如果有一個執行緒保有海量儲存體，則該記憶體無法使用。

## <a name="example"></a>範例

如需使用 `Alloc` 和 `Free` 函數來改善記憶體效能的範例，請參閱[如何：使用配置和免費來改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
