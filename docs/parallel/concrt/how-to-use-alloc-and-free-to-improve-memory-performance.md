---
title: 如何：使用 Alloc 和 Free 改善記憶體效能
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: 8438e833262d42c6083f48f759501c573a35c772
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142793"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 改善記憶體效能

本檔說明如何使用[concurrency：：](reference/concurrency-namespace-functions.md#alloc)配置和[Concurrency：： Free](reference/concurrency-namespace-functions.md#free)函數來改善記憶體效能。 它會比較針對三個不同類型（每個指定 `new` 和 `delete` 運算子），以平行方式反轉陣列元素所需的時間。

當多個執行緒經常同時呼叫 `Alloc` 和 `Free`時，`Alloc` 和 `Free` 函數最有用。 執行時間會為每個執行緒保存個別的記憶體快取;因此，執行時間會管理記憶體，而不會使用鎖定或記憶體屏障。

## <a name="example"></a>範例

下列範例顯示三個類型，分別指定 `new` 和 `delete` 運算子。 `new_delete` 類別使用全域 `new` 和 `delete` 運算子，`malloc_free` 類別使用 C 執行時間[malloc](../../c-runtime-library/reference/malloc.md)和[free](../../c-runtime-library/reference/free.md)函式，而 `Alloc_Free` 類別使用並行執行階段 `Alloc` 和 `Free` 函數。

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>範例

下列範例顯示 `swap` 和 `reverse_array` 函式。 `swap` 函式會在指定的索引處交換陣列的內容。 它會為暫存變數配置堆積中的記憶體。 `reverse_array` 函式會建立大型陣列，並計算以平行方式將該陣列反轉多次所需的時間。

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>範例

下列範例顯示 `wmain` 函式，此函式會計算 `reverse_array` 函數在 `new_delete`、`malloc_free`和 `Alloc_Free` 類型上採取動作所需的時間，每個都使用不同的記憶體配置配置。

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>範例

完整的範例如下所示。

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

這個範例會針對具有四個處理器的電腦產生下列範例輸出。

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

在此範例中，使用 `Alloc` 和 `Free` 函數的類型會提供最佳的記憶體效能，因為 `Alloc` 和 `Free` 函數已針對經常從多個執行緒配置和釋放記憶體區塊進行優化。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `allocators.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc 配置器 .cpp**

## <a name="see-also"></a>另請參閱

[記憶體管理函式](../../parallel/concrt/memory-management-functions.md)<br/>
[配置函式](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 函式](reference/concurrency-namespace-functions.md#free)
