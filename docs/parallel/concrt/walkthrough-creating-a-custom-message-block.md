---
title: 逐步解說：建立自訂訊息區
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: e7dfc5d78d2281d77b9ce882b302c4d7db776d3b
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856989"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>逐步解說：建立自訂訊息區

本文件說明如何建立依優先順序排序內送訊息的自訂訊息區塊類型。

雖然內建訊息區塊類型提供各種功能，您可以建立您自己的訊息區塊類型，並自訂它以符合您的應用程式的需求。 如需 Asynchronous Agents Library 所提供的內建訊息區塊類型的描述，請參閱 <<c0> [ 非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="prerequisites"></a>必要條件

在開始本逐步解說之前，請閱讀下列文件：

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

##  <a name="top"></a> 章節

本逐步解說包含下列各節：

- [設計自訂訊息區](#design)

- [定義 priority_buffer 類別](#class)

- [完整範例](#complete)

##  <a name="design"></a> 設計自訂訊息區

訊息區塊參與傳送和接收訊息的動作。 將訊息傳送的訊息區塊就所謂*來源區塊*。 接收訊息的訊息區塊就所謂*目標區塊*。 同時傳送和接收訊息的訊息區塊就所謂*傳播程式區塊*。 代理程式庫會使用抽象類別[concurrency:: isource](../../parallel/concrt/reference/isource-class.md)表示來源區塊和抽象類別[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)來代表目標區塊。 訊息區塊類型可做為來源衍生自`ISource`; 訊息區塊類型可做為目標，是衍生自`ITarget`。

雖然您可以衍生您的訊息區塊類型，直接從`ISource`和`ITarget`，代理程式庫會定義三個執行的許多功能，是通用於所有的訊息區塊類型，例如處理錯誤的基底類別和連線在訊息區塊一起並行安全的方式。 [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md)類別衍生自`ISource`，並將訊息傳送至其他區塊。 [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md)類別衍生自`ITarget`和從其他區塊接收訊息。 [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md)類別衍生自`ISource`和`ITarget`，並將訊息傳送至其他區塊並從其他區塊接收訊息。 我們建議您使用這三個的基底類別，來處理基礎結構詳細資料，以便您專注於您的訊息區塊的行為。

`source_block`， `target_block`，和`propagator_block`類別會管理連接，或連結的類型、 來源和目標區塊之間和管理訊息的處理方式的型別上參數化的範本。 代理程式庫定義執行連結管理的兩種類型[concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)並[concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。 `single_link_registry`類別可讓訊息區塊連結至一個來源或目標。 `multi_link_registry`類別可讓訊息區塊連結至多個來源或多個目標。 代理程式庫會定義一個類別，會執行訊息管理[concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 `ordered_message_processor`類別可讓它接收依序處理訊息的訊息區塊。

若要進一步了解如何與它們的來源和目標訊息區塊，請考慮下列範例。 此範例中顯示的宣告[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)類別。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`類別衍生自`propagator_block`，並因此做為這兩個來源區塊和目標區塊。 它接受類型的訊息`_Input`，並傳送訊息型別的`_Output`。 `transformer`類別會指定`single_link_registry`做為任何目標區塊連結管理程式和`multi_link_registry`作為任何來源區塊的連線管理員。 因此，`transformer`物件最多可包含一個目標和來源的無限制的數目。

衍生自類別`source_block`六種方法都必須實作： [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets)， [accept_message](reference/source-block-class.md#accept_message)， [reserve_message](reference/source-block-class.md#reserve_message)， [consume_message](reference/source-block-class.md#consume_message)， [release_message](reference/source-block-class.md#release_message)，以及[resume_propagation](reference/source-block-class.md#resume_propagation)。 衍生自類別`target_block`必須實作[propagate_message](reference/propagator-block-class.md#propagate_message)方法，也可以選擇性地實作[send_message](reference/propagator-block-class.md#send_message)方法。 衍生自`propagator_block`相當於衍生自兩者`source_block`和`target_block`。

`propagate_to_any_targets`方法是執行階段呼叫以非同步或同步處理任何傳入的訊息，並傳播出任何外寄訊息。 `accept_message`接受訊息的目標區塊會呼叫方法。 許多訊息區塊類型，例如`unbounded_buffer`，訊息只傳送給會收到它的第一個目標。 因此，它會將擁有權的訊息傳輸至目標。 其他訊息區塊類型，例如[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)，訊息提供給每個目標區塊。 因此，`overwrite_buffer`針對每一個目標建立訊息的複本。

`reserve_message`， `consume_message`， `release_message`，和`resume_propagation`方法可讓訊息區塊參與訊息保留。 目標會封鎖呼叫`reserve_message`方法時提供一則訊息，必須保留以供稍後使用的訊息。 目標區塊保留訊息之後，它可以呼叫`consume_message`方法來取用該訊息或`release_message`取消預定的方法。 如同`accept_message`方法，實作`consume_message`可以傳送訊息的擁有權，或傳回訊息的複本。 在執行階段的目標區塊會耗用或釋放保留的訊息之後，呼叫`resume_propagation`方法。 一般而言，這個方法會繼續訊息傳播，開始在佇列中的下一個訊息。

執行階段呼叫`propagate_message`以非同步方式從另一個區塊的訊息傳輸到目前的方法。 `send_message`方法類似於`propagate_message`，不同之處在於會以同步方式，而不是以非同步方式傳送訊息給目標區塊。 預設實作`send_message`會拒絕所有的內送訊息。 執行階段不會呼叫其中一種方法如果訊息未通過目標區塊相關聯的選擇性篩選函式。 如需訊息篩選條件的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

[[靠上](#top)]

##  <a name="class"></a> 定義 priority_buffer 類別

`priority_buffer`類別是依優先順序，再依接收訊息的順序，先排序內送訊息的自訂訊息區塊類型。 `priority_buffer`類別類似於[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)類別，因為它所保留的訊息，訊息佇列，也因為它做為來源和目標訊息區塊，且可以有多個來源和多個目標。 不過，`unbounded_buffer`基底訊息傳播只在它接收的訊息從其來源的順序。

`priority_buffer`類別會收到訊息類型的 std::[tuple](../../standard-library/tuple-class.md)包含`PriorityType`和`Type`項目。 `PriorityType` 參考型別所在的每個訊息; 優先順序`Type`指的是訊息的資料部分。 `priority_buffer`類別將傳送訊息型別的`Type`。 `priority_buffer`類別也會管理兩個訊息佇列： [std::priority_queue](../../standard-library/priority-queue-class.md)內送訊息的物件和 std::[佇列](../../standard-library/queue-class.md)外寄訊息的物件。 依優先順序排序訊息很有用，當`priority_buffer`物件同時接收多個訊息，或是當它收到多個訊息之前的任何訊息可由取用者讀取。

除了七種方法的類別衍生自`propagator_block`必須實作`priority_buffer`類別也會覆寫`link_target_notification`和`send_message`方法。 `priority_buffer`類別也會定義兩個公用的協助程式方法`enqueue`並`dequeue`，和私用 helper 方法， `propagate_priority_order`。

下列程序描述如何實作`priority_buffer`類別。

#### <a name="to-define-the-prioritybuffer-class"></a>若要定義 priority_buffer 類別

1. 建立C++標頭檔案並將它命名`priority_buffer.h`。 或者，您可以使用現有的標頭檔案是專案的一部分。

1. 在  `priority_buffer.h`，新增下列程式碼。

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 中`std`命名空間中，定義的特製化[std:: less<>](../../standard-library/less-struct.md)並[std:: less](../../standard-library/greater-struct.md)作並行::[訊息](../../parallel/concrt/reference/message-class.md)物件。

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`類別存放區`message`中的物件`priority_queue`物件。 這些類型特製化，讓優先權佇列郵件根據優先順序進行排序。 優先順序是第一個項目`tuple`物件。

1. 在 `concurrencyex`命名空間宣告`priority_buffer`類別。

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 類別衍生自 `propagator_block`。 因此，它可以同時傳送和接收訊息。 `priority_buffer`類別可以有多個目標會接收訊息的型別`Type`。 它也可以傳送訊息的類型的多個來源`tuple<PriorityType, Type>`。

1. 在 `private`一節`priority_buffer`類別中，新增下列成員變數。

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue`物件會保留傳入的訊息;`queue`物件會保留外寄訊息。 A`priority_buffer`物件可以同時接收多個訊息，而`critical_section`物件同步處理的輸入訊息佇列的存取權。

1. 在 `private`區段中，定義複製建構函式和指派運算子。 這可防止`priority_queue`從所指派的物件。

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在 `public`區段中，定義通用的許多訊息區塊類型建構函式。 也定義解構函式。

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在 `public`區段中，定義方法`enqueue`和`dequeue`。 這些協助程式方法會提供傳送和接收訊息之來源的替代方式`priority_buffer`物件。

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. 在 `protected`區段中，定義`propagate_to_any_targets`方法。

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets`方法傳送的訊息，是位於要輸出佇列的輸入佇列，並且將輸出佇列中的所有訊息都傳播出去。

10. 在 `protected`區段中，定義`accept_message`方法。

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   當目標區塊呼叫`accept_message`方法，`priority_buffer`類別會將訊息的擁有權轉移到第一個目標區塊接受它。 (這類似於的行為`unbounded_buffer`。)

11. 在 `protected`區段中，定義`reserve_message`方法。

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`類別允許目標區塊保留訊息，當提供的訊息識別項符合位於佇列前端的訊息識別項。 換句話說，目標可以保留訊息如果`priority_buffer`物件尚未收到額外的訊息和未尚未傳播出目前的金鑰。

12. 在 `protected`區段中，定義`consume_message`方法。

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目標區塊呼叫`consume_message`轉移擁有權，它所保留的訊息。

13. 在 `protected`區段中，定義`release_message`方法。

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目標區塊呼叫`release_message`取消其保留的訊息。

14. 在 `protected`區段中，定義`resume_propagation`方法。

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   執行階段呼叫`resume_propagation`目標區塊會耗用或釋放保留的訊息之後。 這個方法會散佈在輸出佇列中的任何訊息。

15. 在 `protected`區段中，定義`link_target_notification`方法。

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`成員變數由基底類別，定義`source_block`。 此成員變數會指向目標區塊，如果有的話，所保留的訊息，是位於輸出佇列的保留項目。 執行階段會呼叫`link_target_notification`當新的目標連結到`priority_buffer`物件。 這個方法會散佈如果沒有目標持有保留項目，則輸出佇列中的任何訊息。

16. 在 `private`區段中，定義`propagate_priority_order`方法。

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   這個方法會散佈輸出佇列中的所有訊息。 每個訊息在佇列中的供每個目標區塊，直到其中一個目標區塊接受該訊息。 `priority_buffer`類別會保留外寄訊息的順序。 因此，輸出佇列中的第一個訊息必須先接受由目標區塊這個方法提供給目標區塊的任何其他訊息。

17. 在 `protected`區段中，定義`propagate_message`方法。

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`方法可讓`priority_buffer`類別做為訊息接收者，或目標。 這個方法會接收的訊息，提供所提供的來源區塊和優先權佇列中插入該訊息。 `propagate_message`方法然後以非同步方式傳送所有訊息輸出至目標區塊。

   執行階段呼叫這個方法，當您呼叫[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊。

18. 在 `protected`區段中，定義`send_message`方法。

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   `send_message`方法類似於`propagate_message`。 不過，它會傳送輸出訊息，以同步方式而不是以非同步的方式。

   執行階段會呼叫這個方法在同步傳送作業時，例如當您呼叫[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式。

`priority_buffer`類別包含典型的許多訊息區塊類型建構函式多載。 有些建構函式多載採用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)或是[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件，讓訊息區塊受特定工作排程器。 其他建構函式多載會採用篩選函式。 篩選函數可讓訊息區塊接受或拒絕訊息，以根據其內容。 如需訊息篩選條件的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。 如需有關工作排程器的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

因為`priority_buffer`類別會依優先順序排序訊息和接收訊息的順序，由這個類別則最有用收到訊息時以非同步的方式，例如，當您呼叫[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊。

[[靠上](#top)]

##  <a name="complete"></a> 完整的範例

下列範例顯示的完整定義`priority_buffer`類別。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

下列範例同時會執行一些`asend`並[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)上的作業`priority_buffer`物件。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

此範例會產生下列輸出範例。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`類別排序訊息先依優先權然後再由它會接收訊息的順序。 在此範例中，具有更高的數字優先順序的訊息會針對佇列前端插入。

[[靠上](#top)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼並將它貼在 Visual Studio 專案中，或貼上的定義`priority_buffer`類別的檔案中，名為`priority_buffer.h`，以及名為的檔案中的測試程式`priority_buffer.cpp`，然後在 Visual Studio 中執行下列命令命令提示字元 視窗中。

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
