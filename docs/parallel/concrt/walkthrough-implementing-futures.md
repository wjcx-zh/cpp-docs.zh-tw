---
title: 逐步解說：實作未來
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141984"
---
# <a name="walkthrough-implementing-futures"></a>逐步解說：實作未來

本主題說明如何在您的應用程式中執行預期。 本主題示範如何將並行執行階段中的現有功能結合在一起，以執行更多作業。

> [!IMPORTANT]
> 本主題將基於示範目的說明未來的概念。 當您需要計算值供日後使用的非同步工作時，建議您使用[std：：未來](../../standard-library/future-class.md)或[concurrency：： task](../../parallel/concrt/reference/task-class.md) 。

工作*是一種計算*，可以分解成額外、更精細的計算。 *未來*是計算值以供稍後使用的非同步工作。

為了實現未來，本主題會定義 `async_future` 類別。 `async_future` 類別會使用並行執行階段的下列元件： [Concurrency：： task_group](reference/task-group-class.md)類別和[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)類別。 `async_future` 類別使用 `task_group` 類別，以非同步方式計算值，而 `single_assignment` 類別則用來儲存計算的結果。 `async_future` 類別的函式會採用工作函式來計算結果，而 `get` 方法則會抓取結果。

### <a name="to-implement-the-async_future-class"></a>若要實作 async_future 類別

1. 宣告名為 `async_future` 的樣板類別，其會在產生的計算類型上參數化。 將 `public` 和 `private` 區段新增至此類別。

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. 在 `async_future` 類別的 `private` 區段中，宣告 `task_group` 和 `single_assignment` 資料成員。

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. 在 `async_future` 類別的 `public` 區段中，執行此函式。 此函式是在計算結果的工作函式上參數化的範本。 此函式會以非同步方式執行 `task_group` 資料成員中的工作函式，並使用[concurrency：： send](reference/concurrency-namespace-functions.md#send)函式將結果寫入 `single_assignment` 的資料成員。

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. 在 `async_future` 類別的 `public` 區段中，執行「析構函式」。 此析構函式會等候工作完成。

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. 在 `async_future` 類別的 `public` 區段中，執行 `get` 方法。 這個方法會使用[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函式來取出工作函式的結果。

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例會顯示完整的 `async_future` 類別，以及其使用方式的範例。 `wmain` 函式會建立包含10000隨機整數值的 std：：[vector](../../standard-library/vector-class.md)物件。 然後，它會使用 `async_future` 物件來尋找包含在 `vector` 物件中的最小和最大值。

### <a name="code"></a>程式碼

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>註解

這個範例會產生下列輸出：

```Output
smallest: 0
largest:  9999
average:  4981
```

此範例會使用 `async_future::get` 方法來抓取計算的結果。 如果計算仍在使用中，`async_future::get` 方法會等待計算完成。

## <a name="robust-programming"></a>最佳化程式設計

若要擴充 `async_future` 類別以處理工作函式所擲回的例外狀況，請修改 `async_future::get` 方法以呼叫[concurrency：： task_group：： wait](reference/task-group-class.md#wait)方法。 `task_group::wait` 方法會擲回工作函式所產生的任何例外狀況。

下列範例顯示 `async_future` 類別的修改版本。 `wmain` 函式會使用 `try`-`catch` 區塊來列印 `async_future` 物件的結果，或列印工作函式所產生之例外狀況的值。

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

這個範例會產生下列輸出：

```Output
caught exception: error
```

如需並行執行階段中例外狀況處理模型的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `futures.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

**cl/EHsc 先期的後 .cpp**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group 類別](reference/task-group-class.md)<br/>
[single_assignment 類別](../../parallel/concrt/reference/single-assignment-class.md)
