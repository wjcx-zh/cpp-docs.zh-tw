---
title: 如何：使用 Alloc 和 Free 改善記憶體效能
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: e5e5207fe435e73df60b757d4f595aacbb70fe72
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414018"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 改善記憶體效能

本檔說明如何使用 [concurrency：：](reference/concurrency-namespace-functions.md#alloc) 配置和 [Concurrency：： Free](reference/concurrency-namespace-functions.md#free) 函式來改善記憶體效能。 它會比較針對三種不同的類型（每個類型都指定和運算子）進行平行處理陣列元素所需的時間 `new` `delete` 。

`Alloc` `Free` 當多個執行緒經常呼叫和時，和函數最 `Alloc` 有用 `Free` 。 執行時間會為每個執行緒保留個別的記憶體快取;因此，執行時間不會使用鎖定或記憶體阻礙來管理記憶體。

## <a name="example-types-that-specify-new-and-delete-operators"></a>範例：指定 new 和 delete 運算子的類型

下列範例顯示三個型別，每個類型都指定 `new` and `delete` 運算子。 `new_delete`類別會使用 global `new` 和 `delete` 運算子，類別會 `malloc_free` 使用 C 執行時間[malloc](../../c-runtime-library/reference/malloc.md)和[free](../../c-runtime-library/reference/free.md)函式，而 `Alloc_Free` 類別會使用並行執行階段 `Alloc` 和 `Free` 函式。

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example-swap-and-reverse_array-functions"></a>範例：交換和 reverse_array 函式

下列範例顯示 `swap` 和 `reverse_array` 函式。 `swap`函數會在指定的索引處交換陣列的內容。 它會針對暫存變數配置堆積的記憶體。 此函式會 `reverse_array` 建立大型陣列，並計算將該陣列以平行方式反轉的所需時間。

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example-wmain-function"></a>範例： wmain 函數

下列範例顯示的函式 `wmain` 會計算函數處理、和類型所需的時間 `reverse_array` ，而 `new_delete` `malloc_free` `Alloc_Free` 每個都使用不同的記憶體配置配置。

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="complete-code-example"></a>完整的程式碼範例

完整的範例如下。

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

此範例會針對具有四個處理器的電腦產生下列範例輸出。

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

在此範例中，使用和函式的型別 `Alloc` `Free` 會提供最佳的記憶體效能，因為和函式最適合用 `Alloc` `Free` 來從多個執行緒頻繁配置和釋放記憶體區塊。

## <a name="compiling-the-code"></a>編譯程式碼

請複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `allocators.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令。

> **cl.exe/EHsc 配置器 .cpp**

## <a name="see-also"></a>另請參閱

[記憶體管理函數](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc 函式](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 函式](reference/concurrency-namespace-functions.md#free)
