---
title: 如何：使用內容類別實作合作式信號
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 5075052592993f413290242e70206b1e227064aa
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141908"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>如何：使用內容類別實作合作式信號

本主題說明如何使用 concurrency：： CoNtext 類別來執行合作的信號類別。

## <a name="remarks"></a>備註

`Context` 類別可讓您封鎖或產生目前的執行內容。 當目前的內容無法繼續，因為資源無法使用時，封鎖或產生目前的內容會很有用。 *信號*是一種情況的範例，其中目前的執行內容必須等候資源變成可用。 信號（例如重要區段物件）是一個同步處理物件，可讓某個內容中的程式碼具有資源的獨佔存取權。 不過，不同于重要的區段物件，信號可讓一個以上的內容同時存取資源。 如果內容的最大數目包含信號鎖定，則每個額外的內容都必須等候另一個內容釋放鎖定。

### <a name="to-implement-the-semaphore-class"></a>若要執行信號類別

1. 宣告名為 `semaphore`的類別。 將 `public` 和 `private` 區段新增至此類別。

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. 在 `semaphore` 類別的 `private` 區段中，宣告包含信號計數的[std：：](../../standard-library/atomic-structure.md)不可部分完成變數，以及包含必須等候取得信號之內容的[concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)物件。

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. 在 `semaphore` 類別的 `public` 區段中，執行此函式。 此函式會使用 `long long` 值，指定可以同時保留鎖定的內容數目上限。

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. 在 `semaphore` 類別的 `public` 區段中，執行 `acquire` 方法。 這個方法會將信號計數遞減為不可部分完成的作業。 如果信號計數變成負數，請將目前的內容加入至等候佇列的結尾，並呼叫[concurrency：： coNtext：： block](reference/context-class.md#block)方法以封鎖目前的內容。

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. 在 `semaphore` 類別的 `public` 區段中，執行 `release` 方法。 這個方法會以不可部分完成的作業遞增信號計數。 如果信號計數在遞增作業之前為負值，則至少有一個內容正在等候鎖定。 在此情況下，請將等候佇列前端的內容解除封鎖。

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>範例

這個範例中的 `semaphore` 類別會以合作方式運作，因為 `Context::Block` 和 `Context::Yield` 方法會產生執行，讓執行時間可以執行其他工作。

`acquire` 方法會遞減計數器，但可能不會在另一個內容呼叫 `release` 方法之前，完成將內容新增至等候佇列的作業。 為此，`release` 方法會使用會呼叫[concurrency：： CoNtext：： Yield](reference/context-class.md#yield)方法的微調迴圈，以等候 `acquire` 方法完成加入內容。

`release` 方法可以先呼叫 `Context::Unblock` 方法，`acquire` 方法才會呼叫 `Context::Block` 方法。 您不需要防範此競爭條件，因為執行時間允許以任何順序呼叫這些方法。 如果 `release` 方法在 `acquire` 方法針對相同內容呼叫 `Context::Block` 之前呼叫 `Context::Unblock`，該內容會保持解除封鎖。 執行時間只需要對 `Context::Block` 的每個呼叫都與 `Context::Unblock`的對應呼叫相符。

下列範例顯示完整的 `semaphore` 類別。 `wmain` 函式會顯示此類別的基本使用方式。 `wmain` 函式會使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法來建立數個需要存取信號的工作。 因為有三個執行緒可以隨時持有鎖定，所以某些工作必須等候另一個工作完成，並釋放鎖定。

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

這個範例會產生下列範例輸出。

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

如需 `concurrent_queue` 類別的詳細資訊，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。 如需 `parallel_for` 演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `cooperative-semaphore.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc cooperative-semaphore .cpp**

## <a name="robust-programming"></a>最佳化程式設計

您可以使用*資源取得為初始化*（RAII）模式，將 `semaphore` 物件的存取限制為指定的範圍。 在 RAII 模式下，會在堆疊上配置資料結構。 該資料結構會在建立時初始化或取得資源，並在終結資料結構時，終結或釋放該資源。 RAII 模式可保證在封閉範圍結束之前呼叫此析構函式。 因此，當擲回例外狀況或函數包含多個 `return` 語句時，會正確地管理資源。

下列範例會定義名為 `scoped_lock`的類別，其定義于 `semaphore` 類別的 `public` 區段中。 `scoped_lock` 類別與[concurrency：： critical_section：： scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別類似。 `semaphore::scoped_lock` 類別的函式會取得給定 `semaphore` 物件的存取權，而此析構函數會釋放該物件的存取權。

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
下列範例會修改傳遞至 `parallel_for` 演算法的工作函式主體，讓它使用 RAII 來確保在函式傳回之前釋放信號。 這項技術可確保工作函式具有例外狀況安全。

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>另請參閱

[內容](../../parallel/concrt/contexts.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)
