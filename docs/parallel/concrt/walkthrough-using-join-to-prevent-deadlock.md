---
title: 逐步解說：使用聯結以避免死結
ms.date: 11/04/2016
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: b98c2deb158b9b9fc71caa7133aeaeb2acfd369c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498809"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>逐步解說：使用聯結以避免死結

本主題使用哲學家用餐問題，說明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)類別避免應用程式中的死結。 在軟體應用程式中，當兩個或多個處理序都保留資源，且互相等候另一個處理序釋放某些其他資源時，就會發生「死結」。

哲學家用餐問題是在多個並行處理序之間共用一組資源時可能發生的問題的一般集合的特定範例。

## <a name="prerequisites"></a>必要條件

在開始本逐步解說之前，請閱讀下列主題：

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> 章節

本逐步解說包含下列各節：

- [哲學家用餐問題](#problem)

- [實作](#deadlock)

- [使用聯結以避免死結](#solution)

##  <a name="problem"></a> 哲學家用餐問題

哲學家用餐問題，說明如何在應用程式中發生死結。 這個問題，請在五個哲學家坐在圓形桌前。 每個哲學家交替使用思考和吃。 每個哲學家必須分享到左側，而另一個鄰近的 chopstick chopstick 使用右邊的芳鄰。 下圖顯示此版面配置。

![餐廳用餐問題](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")

若要吃，哲學家必須保留兩個筷子。 如果每個哲學家會保留一個 chopstick，正在等候另一個則沒有哲學家可能會用掉，所有變空。

[[靠上](#top)]

##  <a name="deadlock"></a> 實作

下例示範天真的實作哲學家用餐問題。 `philosopher`類別，衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)，可讓每一位哲學家獨立執行動作。 此範例會使用的共用的陣列[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)給予每個物件`philosopher`物件獨佔存取一組筷子的權限。

要關聯至圖例中，實作`philosopher`類別代表一個哲學家。 `int`變數代表每個 chopstick。 `critical_section`物件做為所在 rest 筷子的持有者。 `run`方法模擬生命週期的哲學家。 `think`方法會模擬思考的動作和`eat`方法模擬吃的動作。

A`philosopher`物件鎖定兩者`critical_section`物件來模擬從之前的持有者筷子的權限移除呼叫`eat`方法。 在呼叫之後`eat`，則`philosopher`物件設定為持有者傳回筷子`critical_section`回到解除鎖定狀態的物件。

`pickup_chopsticks`方法說明便會發生死結。 如果每隔`philosopher`物件取得一個鎖定，則不的存取權`philosopher`物件可以繼續，因為其他鎖定由另一個控制`philosopher`物件。

## <a name="example"></a>範例

### <a name="description"></a>描述

### <a name="code"></a>程式碼

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`philosophers-deadlock.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc philosophers-deadlock.cpp**

[[靠上](#top)]

##  <a name="solution"></a> 使用聯結以避免死結

本節說明如何使用訊息緩衝區和訊息傳遞函式，以消除死結的機會。

若要關聯與前一個，本例`philosopher`類別會取代每個`critical_section`所使用的物件[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)物件和`join`物件。 `join`物件做為提供哲學家筷子仲裁程式。

這個範例會使用`unbounded_buffer`類別，因為當目標收到來自訊息`unbounded_buffer`物件，從訊息佇列移除訊息。 這可讓`unbounded_buffer`chopstick 保存的訊息，指出物件是可用。 `unbounded_buffer`物件，不包含任何訊息表示 chopstick 正在使用。

這個範例會使用非窮盡`join`物件，因為非窮盡聯結可讓每個`philosopher`物件至這兩個筷子的存取權時，才兩者`unbounded_buffer`物件包含一則訊息。 窮盡聯結不會使死結，因為窮盡聯結接受訊息，因為它們變成可用。 如果所有 greedy （窮盡），便會發生死結`join`物件收到訊息，但是永久等待，另一個則變成可用。

如需 greedy （窮盡） 和非窮盡聯結和各種不同的訊息緩衝區類型之間的差異的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

#### <a name="to-prevent-deadlock-in-this-example"></a>若要避免在此範例中的死結

1. 移除此範例中的下列程式碼。

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. 變更的型別`_left`並`_right`的資料成員`philosopher`類別`unbounded_buffer`。

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. 修改`philosopher`建構函式才會`unbounded_buffer`物件做為其參數。

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. 修改`pickup_chopsticks`方法，以使用非窮盡`join`從這兩個筷子的訊息緩衝區接收訊息的物件。

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. 修改`putdown_chopsticks`方法，以將訊息傳送至這兩個筷子的訊息緩衝區釋放筷子的存取。

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. 修改`run`方法來保存的結果`pickup_chopsticks`方法，並將傳遞至這些結果`putdown_chopsticks`方法。

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. 修改的宣告`chopsticks`變數中`wmain`函式必須是陣列的`unbounded_buffer`每個都容納一則訊息的物件。

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下圖顯示完成的範例使用非窮盡`join`物件，以解決死結的風險。

### <a name="code"></a>程式碼

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

### <a name="comments"></a>註解

此範例會產生下列輸出。

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`philosophers-join.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc philosophers-join.cpp**

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)
