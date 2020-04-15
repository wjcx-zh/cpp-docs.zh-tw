---
title: 逐步解說：建立自訂訊息區
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368564"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>逐步解說：建立自訂訊息區

本文件介紹如何創建按優先順序對傳入郵件進行排序的自定義消息塊類型。

儘管內置的消息塊類型提供了廣泛的功能,但您可以創建自己的消息塊類型並對其進行自定義以滿足應用程式的要求。 有關非同步代理庫提供的內建訊息區類型的說明,請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)塊 。

## <a name="prerequisites"></a>Prerequisites

在開始本演練之前,請閱讀以下文件:

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>部分

本逐步解說包含下列各節：

- [設計自訂訊息區](#design)

- [定義priority_buffer類](#class)

- [完整範例](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>設計自訂訊息區

消息塊參與發送和接收消息的行為。 傳送訊息訊息塊稱為*來源區塊*。 接收訊息的訊息塊稱為*目標塊*。 傳送及接收訊息的訊息的訊息為*傳播器塊*。 代理庫使用抽象類[併發::iSource](../../parallel/concrt/reference/isource-class.md)表示源塊和抽象類[併發::iTarget](../../parallel/concrt/reference/itarget-class.md)表示目標塊。 充當源的訊息塊型態派`ISource`生自 。充當目標的訊息塊型態派`ITarget`生自 。

儘管可以直接從`ISource`和`ITarget`派生消息塊類型,但代理庫定義了三個基類,它們執行所有消息塊類型共有的大部分功能,例如,以併發安全的方式處理錯誤和將消息塊連接在一起。 [併發::source_block](../../parallel/concrt/reference/source-block-class.md)類派生`ISource`併 發送消息到其他塊。 [併發::target_block](../../parallel/concrt/reference/target-block-class.md)類派生`ITarget`自 其他塊並接收消息。 [併發::p羅帕器_block](../../parallel/concrt/reference/propagator-block-class.md)類派生`ISource`自`ITarget`並將 消息發送到其他塊,它接收來自其他塊的消息。 我們建議您使用這三個基類來處理基礎結構詳細資訊,以便您可以專注於消息塊的行為。

`target_block`和`source_block`類是在管理源和目標塊之間的連接或連結的類型以及管理消息處理方式的類型上參數`propagator_block`化的範本。 代理庫定義了兩種執行連結管理的類型,[併發::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)[併發:multi_link_registry。](../../parallel/concrt/reference/multi-link-registry-class.md) 該`single_link_registry`類使消息塊能夠連結到一個源或一個目標。 該`multi_link_registry`類使消息塊能夠連結到多個源或多個目標。 代理庫定義執行訊息管理的類別,[並發::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 類`ordered_message_processor`使消息塊能夠按接收消息的順序處理消息。

為了更好地瞭解消息塊與其源和目標的關係,請考慮以下示例。 此示例顯示[併發::轉換器](../../parallel/concrt/reference/transformer-class.md)類的聲明。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

類`transformer`派生`propagator_block`自 ,因此同時充當源塊和目標塊。 它接受型`_Input`態 的訊息並`_Output`傳送型態的訊息 。 類`transformer``single_link_registry`指定 為任何目標塊的連結管理員`multi_link_registry`,並指定為任何源塊的連結管理員。 因此,一`transformer`個物件最多只能有一個目標和無限數量的源。

派生自`source_block`的類必須實現六種方法:propagate_to_any_targets、accept_message、reserve_message、consume_message、release_message[release_message](reference/source-block-class.md#release_message)[reserve_message](reference/source-block-class.md#reserve_message)和[resume_propagation。](reference/source-block-class.md#resume_propagation) [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets) [accept_message](reference/source-block-class.md#accept_message) [consume_message](reference/source-block-class.md#consume_message) 派生自`target_block`的類必須實現[propagate_message](reference/propagator-block-class.md#propagate_message)方法,並且可以選擇實現[send_message](reference/propagator-block-class.md#send_message)方法。 衍生功能`propagator_block`上等效於派生從與`source_block``target_block`。

運行時`propagate_to_any_targets`調用該方法以非同步或同步處理任何傳入消息並傳播出任何傳出消息。 目標`accept_message`塊調用該方法以接受消息。 許多消息塊類型(如`unbounded_buffer`)僅向接收消息的第一個目標發送消息。 因此,它將消息的擁有權轉移到目標。 其他消息塊類型(如[併發::overwrite_buffer)](../../parallel/concrt/reference/overwrite-buffer-class.md)向其每個目標塊提供消息。 因此,`overwrite_buffer`為其每個目標創建消息的副本。

、`resume_propagation`方法使消息塊能夠參與消息保留。 `reserve_message` `consume_message` `release_message` 當 Target`reserve_message`塊收到消息時調用該方法,並且必須保留消息供以後使用。 目標塊保留消息后,它可以調用`consume_message`方法以使用該消息或取消`release_message`保留 的方法。 與方法`accept_message`一樣,實現`consume_message`可以轉移消息的擁有權或返回消息的副本。 在目標塊使用或釋放保留消息后,運行時將調用`resume_propagation`方法。 通常,此方法繼續消息傳播,從佇列中的下一條消息開始。

運行時調用`propagate_message`該方法以非同步方式將消息從另一個塊傳輸到當前塊。 該方法`send_message`類似`propagate_message`於 ,只不過它是同步的,而不是非同步的,將消息發送到目標塊。 的`send_message`默認實現拒絕所有傳入消息。 如果消息未傳遞與目標塊關聯的可選篩選器函數,則運行時不會調用這些方法中的任何一個。 關於訊息篩選器的詳細資訊,請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)塊 。

【[頂端](#top)

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>定義priority_buffer類

類`priority_buffer`是一種自定義消息塊類型,它首先按優先順序對傳入郵件進行排序,然後按接收消息的順序排序。 類`priority_buffer`類似於[併發::unbounded_buffer](reference/unbounded-buffer-class.md)類,因為它包含消息佇列,也因為它同時充當源和目標消息塊,可以同時具有多個源和多個目標。 但是,`unbounded_buffer`消息傳播僅基於消息從其源接收消息的順序。

類別`priority_buffer`接收為 std 訊息:`PriorityType`包含`Type`與元素的[中陣列](../../standard-library/tuple-class.md)。 `PriorityType`指保存每條消息優先順序的類型;`Type`引用消息的數據部分。 類別`priority_buffer`傳送`Type`型態的訊息 。 這個`priority_buffer`類別管理兩個訊息佇列:傳入訊息的[std::priity_queue](../../standard-library/priority-queue-class.md)物件和用於傳出訊息的 std:[佇列物件](../../standard-library/queue-class.md)。 當`priority_buffer`物件同時接收多條消息或在消費者讀取任何消息之前接收多條消息時,按優先順序排序消息非常有用。

除了`propagator_block`派生自類必須實現的七種方法`priority_buffer`外 ,類還重`link_target_notification`寫`send_message`和 方法。 這個`priority_buffer`類別定義兩個公共說明器方法,`enqueue`與`dequeue`與與 .`propagate_priority_order`與一個私有說明器方法 。

以下過程介紹如何實現類`priority_buffer`。

#### <a name="to-define-the-priority_buffer-class"></a>定義priority_buffer類

1. 建立 C++標頭檔並命名`priority_buffer.h`它。 或者,您可以使用作為專案一部分的現有標頭檔。

1. 在`priority_buffer.h`中,添加以下代碼。

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 在命名`std`空間中,定義[std:::less](../../standard-library/less-struct.md)和[std:::大於](../../standard-library/greater-struct.md)對併發作用的專門化:[消息](../../parallel/concrt/reference/message-class.md)物件。

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   類別`priority_buffer`儲存`message`物件在物件中`priority_queue`。 這些類型專門化使優先順序佇列能夠根據郵件的優先順序對消息進行排序。 優先順序是物件的第一個`tuple`元素。

1. 在命名`concurrencyex`空間中,宣告類別`priority_buffer`。

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 類別衍生自 `propagator_block`。 因此,它可以發送和接收消息。 類`priority_buffer`可以有多個目標來接收`Type`類型 的消息。 它還可以有多個源,發送類型`tuple<PriorityType, Type>`的消息。

1. 在`private`類的部分`priority_buffer`中,添加以下成員變數。

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   物件`priority_queue`保存傳入消息;物件`queue`保存傳出消息。 對`priority_buffer`象 可以同時接收多條消息;物件`critical_section`同步對輸入消息佇列的訪問。

1. 在部分`private`中,定義複製構造函數和賦值運算符。 這可以防止`priority_queue`物件被分配。

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在本節`public`中,定義許多消息塊類型共有的構造函數。 還定義析構函數。

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在`public`部份中,定義方法和`enqueue``dequeue`。 這些説明程式方法提供了向`priority_buffer`物件發送消息和接收來自物件的消息的替代方法。

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. 在部分`protected`中,`propagate_to_any_targets`定義方法。

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   該方法`propagate_to_any_targets`將輸入佇列前面的消息傳輸到輸出佇列,並傳播輸出佇列中的所有消息。

1. 在部分`protected`中,`accept_message`定義方法。

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   當目標塊調用`accept_message`該方法時`priority_buffer`, 類將消息的所有權轉移到接受它的第一個目標塊。 (這類似於`unbounded_buffer`.) 的行為。

1. 在部分`protected`中,`reserve_message`定義方法。

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   當`priority_buffer`提供的消息標識碼與佇列前面的消息標識符匹配時,類允許目標塊保留消息。 換句話說,如果物件尚未收到其他消息但尚未傳播出當前`priority_buffer`消息,則目標可以保留該消息。

1. 在部分`protected`中,`consume_message`定義方法。

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目標塊調用`consume_message`以轉移它保留的消息的擁有權。

1. 在部分`protected`中,`release_message`定義方法。

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目標塊調用`release_message`以取消其對消息的保留。

1. 在部分`protected`中,`resume_propagation`定義方法。

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   目標塊使用或`resume_propagation`釋放保留消息之後的運行時調用。 此方法傳播輸出佇列中的任何消息。

1. 在部分`protected`中,`link_target_notification`定義方法。

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   成員`_M_pReservedFor`變數由基類別`source_block`定義 。 此成員變數指向目標塊(如果有),該塊對輸出佇列前面的消息保留。 當新目標連結到`link_target_notification`物件時`priority_buffer`, 執行時呼叫。 如果沒有目標保留,此方法會傳播輸出佇列中的任何消息。

1. 在部分`private`中,`propagate_priority_order`定義方法。

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   此方法從輸出佇列中傳播所有消息。 佇列中的每個消息都提供給每個目標塊,直到其中一個目標塊接受該消息。 類`priority_buffer`保留傳出消息的順序。 因此,在此方法向目標塊提供任何其他消息之前,目標塊必須接受輸出佇列中的第一條消息。

1. 在部分`protected`中,`propagate_message`定義方法。

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   該方法`propagate_message``priority_buffer`使 類能夠充當消息接收者或目標。 此方法接收提供的源塊提供的消息,並將該消息插入到優先順序佇列中。 然後`propagate_message`,該方法異步地將所有輸出消息發送到目標塊。

   當您調用[併發::asend](reference/concurrency-namespace-functions.md#asend)函數或消息塊連接到其他消息塊時,運行時調用此方法。

1. 在部分`protected`中,`send_message`定義方法。

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   此方法`send_message`類似`propagate_message`。 但是,它同步而不是非同步發送輸出消息。

   運行時在同步發送操作期間調用此方法,例如調用[併發:::發送](reference/concurrency-namespace-functions.md#send)函數時。

類`priority_buffer`包含構造函數重載,這些重載是許多消息塊類型中常見的。 某些構造函數重載採用[併發::計劃程式](../../parallel/concrt/reference/scheduler-class.md)或[併發::計劃組](../../parallel/concrt/reference/schedulegroup-class.md)物件,使消息塊能夠由特定的任務調度程式管理。 其他構造函數重載採用篩選器函數。 篩選器功能使消息塊能夠根據其負載接受或拒絕消息。 關於訊息篩選器的詳細資訊,請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)塊 。 有關工作計劃程式的詳細資訊,請參閱[工作計畫程式](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

由於`priority_buffer`類按優先順序排序,然後按接收消息的順序排序,因此在異步接收消息時(例如,當您調用[併發::asend](reference/concurrency-namespace-functions.md#asend)函數或消息塊連接到其他消息塊時)時,該類最有用。

【[頂端](#top)

## <a name="the-complete-example"></a><a name="complete"></a>完整範例

下面的示例顯示了`priority_buffer`類的完整定義。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

以下示例同時執行多個`asend`[併發::接收](reference/concurrency-namespace-functions.md#receive)`priority_buffer`物件上的操作。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

此示例生成以下範例輸出。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

類`priority_buffer`首先按優先順序排序消息,然後按接收消息的順序排序。 在此示例中,具有更大數位優先順序的消息插入到佇列的前面。

【[頂端](#top)

## <a name="compiling-the-code"></a>編譯程式碼

複製範例代碼並將其貼上到 Visual Studio 專案中`priority_buffer`,或將 類的定義貼上`priority_buffer.h`到已命名的檔案中,並將測試程式`priority_buffer.cpp`貼上到名為的檔案中,然後在 Visual Studio 命令提示視窗中執行以下命令。

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>另請參閱

[併發運行時演練](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)
