---
title: 逐步解說：使用聯結以避免死結
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 5bdd6cd81051d224714dd66d4604cbdec4ddb552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217879"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>逐步解說：使用聯結以避免死結

本主題使用哲學家就餐問題，說明如何使用[concurrency：： join](../../parallel/concrt/reference/join-class.md)類別來避免應用程式中發生鎖死。 在軟體應用程式中，當兩個或多個處理序都保留資源，且互相等候另一個處理序釋放某些其他資源時，就會發生「死結」**。

哲學家就餐問題是在多個並行進程之間共用一組資源時，可能會發生的一組一般問題的特定範例。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列主題：

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [逐步解說：建立以代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>各節

本逐步解說包含下列各節：

- [哲學家用餐問題](#problem)

- [簡單的執行](#deadlock)

- [使用聯結來防止鎖死](#solution)

## <a name="the-dining-philosophers-problem"></a><a name="problem"></a>哲學家就餐問題

哲學家就餐問題說明如何在應用程式中發生鎖死。 在此問題中，有五個哲學家位於一個圓形資料表上。 每個哲學家都會在思考與吃時改變。 每個哲學家都必須與左邊的鄰近處共用一個 chopstick，並將另一個 chopstick 與右邊的鄰近。 下圖顯示此版面配置。

![哲學家用餐問題](../../parallel/concrt/media/dining_philosophersproblem.png "哲學家用餐問題")

哲學家必須擁有兩個 chopsticks，才能吃。 如果每個哲學家只保留一個 chopstick，而且正在等候另一個，則不會有任何哲學家可以吃和所有使。

[[頂端](#top)]

## <a name="a-nave-implementation"></a><a name="deadlock"></a>簡單的執行

下列範例顯示哲學家就餐問題的簡單實現。 `philosopher`衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)的類別可讓每個哲學家獨立動作。 此範例使用[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)物件的共用陣列，為每個 `philosopher` 物件提供一對 chopsticks 的獨佔存取權。

為了使執行與圖例產生關聯， `philosopher` 類別代表一個哲學家。 **`int`** 變數代表每個 chopstick。 `critical_section`物件會作為 chopsticks rest 的持有者。 `run`方法會模擬哲學家的生命週期。 `think`方法會模擬思考動作，而方法會 `eat` 模擬吃的動作。

`philosopher`物件會鎖定這兩個 `critical_section` 物件，以模擬在呼叫方法之前，從持有者移除 chopsticks `eat` 。 呼叫之後 `eat` ， `philosopher` 物件會將物件設回已解除鎖定的狀態，以將 chopsticks 傳回給持有者 `critical_section` 。

`pickup_chopsticks`方法會說明發生鎖死的位置。 如果每個 `philosopher` 物件都取得其中一個鎖定的存取權，則沒有任何 `philosopher` 物件可以繼續，因為其他鎖定是由另一個物件所控制 `philosopher` 。

### <a name="example"></a>範例

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `philosophers-deadlock.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc philosophers-deadlock.cpp .cpp**

[[頂端](#top)]

## <a name="using-join-to-prevent-deadlock"></a><a name="solution"></a>使用聯結來防止鎖死

本節說明如何使用訊息緩衝區和訊息傳遞函式來消除鎖死的機率。

為了讓這個範例與先前的實例產生關聯， `philosopher` 類別會 `critical_section` 使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)物件和物件來取代每個物件 `join` 。 `join`物件會做為提供 chopsticks 至哲學家的仲裁程式。

這個範例會使用 `unbounded_buffer` 類別，因為當目標從物件接收訊息時 `unbounded_buffer` ，訊息會從訊息佇列中移除。 這可讓 `unbounded_buffer` 保存訊息的物件指出 chopstick 可供使用。 `unbounded_buffer`不包含任何訊息的物件表示正在使用 chopstick。

這個範例會使用非貪婪 `join` 物件，因為非貪婪聯結 `philosopher` 只會在兩個物件都包含訊息時，讓每個物件都能存取這兩個 chopsticks `unbounded_buffer` 。 貪婪聯結不會防止鎖死，因為貪婪聯結會在訊息可供使用時立即接受。 如果所有的貪婪物件都 `join` 收到其中一個訊息，但是永遠等待另一個訊息變成可用，就會發生鎖死。

如需有關貪婪和非貪婪聯結的詳細資訊，以及各種訊息緩衝區類型之間的差異，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

### <a name="to-prevent-deadlock-in-this-example"></a>避免在此範例中發生鎖死

1. 從範例中移除下列程式碼。

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. 將 `_left` 類別的和資料成員的類型變更 `_right` `philosopher` 為 `unbounded_buffer` 。

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. 修改此函式， `philosopher` 將 `unbounded_buffer` 物件當做其參數。

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. 修改 `pickup_chopsticks` 方法以使用非貪婪 `join` 物件，從這兩個 chopsticks 的訊息緩衝區接收訊息。

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. 將 `putdown_chopsticks` 訊息傳送至兩個 chopsticks 的訊息緩衝區，以修改方法以釋放 chopsticks 的存取權。

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. 修改 `run` 方法以保存方法的結果 `pickup_chopsticks` ，並將這些結果傳遞給 `putdown_chopsticks` 方法。

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. 修改函 `chopsticks` 式中變數的宣告 `wmain` ，使其成為 `unbounded_buffer` 每個保留一則訊息的物件陣列。

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>說明

以下顯示使用非貪婪物件的完整範例， `join` 以消除鎖死的風險。

### <a name="example"></a>範例

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

此範例會產生下列輸出。

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

### <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `philosophers-join.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc philosophers-join .cpp**

[[頂端](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)
