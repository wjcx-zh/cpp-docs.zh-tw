---
title: 逐步解說：實作 Future
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 7164919d649751ac11fefa5be3cb2e5b7798ee4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407844"
---
# <a name="walkthrough-implementing-futures"></a>逐步解說：實作 Future

本主題說明如何在您的應用程式中實作 future。 本主題示範如何結合現有的功能在並行執行階段成可執行其他作業。

> [!IMPORTANT]
>  本主題將基於示範目的說明未來的概念。 我們建議您改用[std](../../standard-library/future-class.md)或是[concurrency:: task](../../parallel/concrt/reference/task-class.md)當您需要計算值，以供稍後使用的非同步工作。

A*任務*是能分解成其他、 更精細的計算的計算。 A*未來*是非同步工作的計算值，以供稍後使用。

若要實作 future，本主題定義`async_future`類別。 `async_future`類別會使用這些並行執行階段元件： [concurrency:: task_group](reference/task-group-class.md)類別和[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)類別。 `async_future`類別會使用`task_group`類別來以非同步方式計算值和`single_assignment`類別來儲存計算的結果。 建構函式`async_future`類別會計算結果，將工作函式和`get`方法會擷取結果。

### <a name="to-implement-the-asyncfuture-class"></a>若要實作 async_future 類別

1. 宣告樣板類別，名為`async_future`參數化的產生的計算類型。 新增`public`和`private`區段，以這個類別。

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. 在 `private`一節`async_future`類別中，宣告`task_group`和`single_assignment`資料成員。

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. 在 `public`一節`async_future`類別，請實作建構函式。 建構函式會是計算結果的工作函式參數化的範本。 建構函式以非同步方式執行中的工作函式`task_group`資料成員，並使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式來將結果寫入`single_assignment`資料成員。

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. 在 `public`一節`async_future`類別，請實作解構函式。 解構函式會等候工作完成。

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. 在 `public`一節`async_future`類別，請實作`get`方法。 這個方法會使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式來擷取工作函式的結果。

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例示範完整`async_future`類別和其用法範例。 `wmain`函式會建立 std::[向量](../../standard-library/vector-class.md)包含 10,000 的隨機整數值的物件。 然後它會使用`async_future`若要尋找最小和最大值中所包含的物件`vector`物件。

### <a name="code"></a>程式碼

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>註解

這個範例會產生下列輸出：

```Output
smallest: 0
largest:  9999
average:  4981
```

此範例會使用`async_future::get`方法來擷取計算的結果。 `async_future::get`方法會等候完成計算是否仍在作用中的計算。

## <a name="robust-programming"></a>穩固程式設計

擴充`async_future`類別來處理工作函式所擲回的例外狀況中，修改`async_future::get`方法來呼叫[2&gt;concurrency::task_group::wait&lt;2](reference/task-group-class.md#wait)方法。 `task_group::wait`方法會擲回任何例外狀況所產生的工作函式。

下列範例示範的修改的版本`async_future`類別。 `wmain`函式會使用`try` - `catch`區塊的結果列印在`async_future`物件，或是要列印的工作函式所產生的例外狀況的值。

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

這個範例會產生下列輸出：

```Output
caught exception: error
```

如需有關並行執行階段的例外狀況處理模型的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`futures.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc futures.cpp**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group 類別](reference/task-group-class.md)<br/>
[single_assignment 類別](../../parallel/concrt/reference/single-assignment-class.md)
