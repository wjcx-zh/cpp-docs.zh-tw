---
title: HOW TO：使用 Alloc 和 Free 改善記憶體效能
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: f55bf360ac2b4c7162c1ed2b917ac6ce8c7cd11f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410015"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>HOW TO：使用 Alloc 和 Free 改善記憶體效能

本文件說明如何使用[concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)並[concurrency:: free](reference/concurrency-namespace-functions.md#free)函式來改善記憶體效能。 它會比較時間所需的三種不同類型，反轉平行陣列的項目指定每個`new`和`delete`運算子。

`Alloc`並`Free`函式在多個執行緒經常呼叫時會最有用`Alloc`和`Free`。 執行階段會保存不同的記憶體快取的每個執行緒中;因此，執行階段會管理記憶體，而不使用鎖定或記憶體屏障。

## <a name="example"></a>範例

下列範例示範三種類型，每個指定`new`和`delete`運算子。 `new_delete`類別會使用全域`new`並`delete`運算子`malloc_free`類別會使用 C 執行階段[malloc](../../c-runtime-library/reference/malloc.md)並[免費](../../c-runtime-library/reference/free.md)函式，和`Alloc_Free`類別會使用並行執行階段`Alloc`和`Free`函式。

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>範例

下列範例顯示 `swap` 和 `reverse_array` 函式。 `swap`函式會交換的指定索引處之陣列的內容。 它會從暫存變數的堆積配置記憶體。 `reverse_array`函式會建立大型的陣列，並計算反向數次以平行方式該陣列所需的時間。

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>範例

下列範例所示`wmain`函式，用來計算所需的時間`reverse_array`函式來處理`new_delete`， `malloc_free`，和`Alloc_Free`類型，它們分別使用不同的記憶體配置方案。

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>範例

完整的範例如下。

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

此範例會產生下列範例輸出適用於具有四個處理器的電腦。

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

在此範例中，使用類型`Alloc`並`Free`函式會提供最佳的記憶體內部效能，因為`Alloc`和`Free`函式最適合用於經常配置及釋放記憶體，從多個區塊執行緒。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`allocators.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc allocators.cpp**

## <a name="see-also"></a>另請參閱

[記憶體管理函式](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc 函式](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 函式](reference/concurrency-namespace-functions.md#free)
