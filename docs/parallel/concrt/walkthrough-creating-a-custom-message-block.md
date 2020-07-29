---
title: 逐步解說：建立自訂訊息區
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: f95eaf7e1da41bd473ab15d12330d0177b98ccdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219491"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>逐步解說：建立自訂訊息區

本檔描述如何建立依優先順序排序傳入訊息的自訂訊息區塊類型。

雖然內建的訊息區塊類型提供各式各樣的功能，您還是可以建立自己的訊息區塊類型，並加以自訂以符合應用程式的需求。 如需非同步代理程式程式庫所提供之內建訊息區塊類型的說明，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列檔：

- [非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>各節

本逐步解說包含下列各節：

- [設計自訂訊息區塊](#design)

- [定義 priority_buffer 類別](#class)

- [完整範例](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>設計自訂訊息區塊

訊息區塊會參與傳送和接收訊息的動作。 傳送訊息的訊息區塊稱為「*來源區塊*」。 接收訊息的訊息區塊稱為「*目標區塊*」。 傳送和接收訊息的訊息區塊稱為「*傳播程式區塊*」。 代理程式程式庫會使用抽象類別[concurrency：： ISource](../../parallel/concrt/reference/isource-class.md)來代表來源區塊，以及抽象類別[Concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md)來表示目標區塊。 當做來源衍生自的訊息區塊類型 `ISource` ; 作為目標的訊息區塊類型會衍生自 `ITarget` 。

雖然您可以直接從和衍生您的訊息區塊類型，但代理程式連結 `ISource` `ITarget` 庫會定義三個基類，以執行所有訊息區塊類型通用的許多功能，例如，處理錯誤，以及以並行安全方式將訊息區塊連接在一起。 [Concurrency：： source_block](../../parallel/concrt/reference/source-block-class.md)類別衍生自 `ISource` ，並將訊息傳送至其他區塊。 [Concurrency：： target_block](../../parallel/concrt/reference/target-block-class.md)類別衍生自 `ITarget` ，並從其他區塊接收訊息。 [Concurrency：:p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md)類別衍生自 `ISource` 和 `ITarget` ，並將訊息傳送至其他區塊，並從其他區塊接收訊息。 建議您使用這三個基類來處理基礎結構的詳細資料，讓您可以專注于訊息區塊的行為。

`source_block`、 `target_block` 和 `propagator_block` 類別是在類型上參數化的範本，可管理來源與目標區塊之間的連接或連結，以及管理訊息處理方式的類型。 代理程式程式庫會定義兩個類型，以執行連結管理， [concurrency：： single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)和[concurrency：： multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。 `single_link_registry`類別可讓訊息區塊連結至一個來源或一個目標。 `multi_link_registry`類別可讓訊息區塊連結至多個來源或多個目標。 代理程式程式庫會定義一個執行訊息管理的類別，也就是[concurrency：： ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 `ordered_message_processor`類別可讓訊息區塊依接收訊息的順序進行處理。

若要進一步瞭解訊息區塊與其來源和目標之間的關聯，請考慮下列範例。 這個範例會顯示[concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)類別的宣告。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`類別衍生自 `propagator_block` ，因此可同時做為來源區塊和目標區塊。 它接受類型的訊息 `_Input` ，並傳送類型為的訊息 `_Output` 。 類別會指定做為任何 `transformer` `single_link_registry` 目標區塊的連結管理員，以及做為 `multi_link_registry` 任何來源區塊的連結管理員。 因此，一個 `transformer` 物件最多可以有一個目標和無限數量的來源。

衍生自的類別 `source_block` 必須執行六個方法： [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets)、 [accept_message](reference/source-block-class.md#accept_message)、 [reserve_message](reference/source-block-class.md#reserve_message)、 [consume_message](reference/source-block-class.md#consume_message)、 [release_message](reference/source-block-class.md#release_message)和[resume_propagation](reference/source-block-class.md#resume_propagation)。 衍生自的類別 `target_block` 必須執行[propagate_message](reference/propagator-block-class.md#propagate_message)方法，而且可以選擇性地執行[send_message](reference/propagator-block-class.md#send_message)方法。 衍生自的 `propagator_block` 功能相當於衍生自 `source_block` 和 `target_block` 。

`propagate_to_any_targets`執行時間會呼叫方法，以非同步或同步處理任何傳入的訊息，並傳播任何外寄訊息。 `accept_message`目標區塊會呼叫方法以接受訊息。 許多訊息區塊類型（例如 `unbounded_buffer` ）只會將訊息傳送到接收它的第一個目標。 因此，它會將訊息的擁有權轉移給目標。 其他訊息區塊類型，例如[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)，會提供訊息給它的每個目標區塊。 因此，會 `overwrite_buffer` 為每一個目標建立訊息的複本。

`reserve_message`、 `consume_message` 、 `release_message` 和 `resume_propagation` 方法可讓訊息區塊參與訊息保留。 目標區塊 `reserve_message` 會在收到訊息時呼叫方法，而且必須保留訊息以供稍後使用。 在目標區塊保留訊息之後，它可以呼叫 `consume_message` 方法來取用該訊息，或使用 `release_message` 方法來取消保留。 如同 `accept_message` 方法，的執行 `consume_message` 可以傳送訊息的擁有權，或傳回訊息的複本。 在目標區塊使用或釋放保留的訊息之後，執行時間會呼叫 `resume_propagation` 方法。 一般來說，這個方法會繼續訊息傳播，從佇列中的下一個訊息開始。

執行時間會呼叫 `propagate_message` 方法，以非同步方式將訊息從另一個區區塊轉送到目前的區塊。 `send_message`方法類似于 `propagate_message` ，不同之處在于它會同步而不是以非同步方式將訊息傳送至目標區塊。 的預設執行會 `send_message` 拒絕所有傳入的訊息。 如果訊息未傳遞與目標區塊相關聯的選擇性篩選函數，執行時間就不會呼叫其中一個方法。 如需訊息篩選器的詳細資訊，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

[[頂端](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>定義 priority_buffer 類別

`priority_buffer`類別是自訂的訊息區塊型別，它會先依優先順序排序內送訊息，再依接收訊息的順序排序。 `priority_buffer`類別與[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)類別類似，因為它會保存訊息佇列，同時也會做為來源和目標訊息區塊，而且可以同時擁有多個來源和多個目標。 不過， `unbounded_buffer` 只會根據接收訊息來源的順序，將訊息傳播做為基礎。

`priority_buffer`類別會接收類型為 std：：[元組](../../standard-library/tuple-class.md)的訊息，其中包含 `PriorityType` 和 `Type` 元素。 `PriorityType`參考保存每個訊息之優先順序的類型;`Type`參考訊息的資料部分。 類別會傳送 `priority_buffer` 類型為的訊息 `Type` 。 `priority_buffer`類別也會管理兩個訊息佇列：內送訊息的[std：:p riority_queue](../../standard-library/priority-queue-class.md)物件，以及外寄訊息的 std：：[queue](../../standard-library/queue-class.md)物件。 當物件在取用 `priority_buffer` 者讀取任何訊息之前，同時收到多則訊息或接收多個訊息時，依優先順序排序訊息就很有用。

除了必須實作為衍生自之類別的七個方法之外 `propagator_block` ， `priority_buffer` 類別也會覆寫 `link_target_notification` 和 `send_message` 方法。 `priority_buffer`類別也會定義兩個公用 helper 方法： `enqueue` 和，以及 `dequeue` 私用 helper 方法 `propagate_priority_order` 。

下列程式描述如何執行 `priority_buffer` 類別。

#### <a name="to-define-the-priority_buffer-class"></a>若要定義 priority_buffer 類別

1. 建立 c + + 標頭檔，並將它命名為 `priority_buffer.h` 。 或者，您可以使用屬於專案的現有標頭檔。

1. 在中 `priority_buffer.h` ，加入下列程式碼。

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 在 `std` 命名空間中，定義對 concurrency：：[message](../../parallel/concrt/reference/message-class.md)物件採取動作之[std：： less](../../standard-library/less-struct.md)和[std：：大於](../../standard-library/greater-struct.md)的特製化。

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`類別會將 `message` 物件儲存在 `priority_queue` 物件中。 這些型別特製化可讓優先順序佇列根據其優先順序來排序訊息。 優先順序是物件的第一個元素 `tuple` 。

1. 在 `concurrencyex` 命名空間中，宣告 `priority_buffer` 類別。

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 類別衍生自 `propagator_block`。 因此，它可以傳送和接收訊息。 `priority_buffer`類別可以有多個目標，以接收類型為的訊息 `Type` 。 它也可以有多個來源，以傳送類型為的訊息 `tuple<PriorityType, Type>` 。

1. 在 **`private`** 類別的區段中 `priority_buffer` ，加入下列成員變數。

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   物件會保存內送 `priority_queue` 訊息; `queue` 物件會保留外寄訊息。 `priority_buffer`物件可以同時接收多個訊息; `critical_section` 物件會同步處理輸入訊息佇列的存取。

1. 在 **`private`** 區段中，定義複製的「函數」和「指派運算子」。 這可避免 `priority_queue` 物件被指派。

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在 **`public`** 區段中，定義許多訊息區塊類型通用的函式。 同時定義析構函式。

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在 **`public`** 區段中，定義方法 `enqueue` 和 `dequeue` 。 這些 helper 方法提供了另一種方式，可將訊息傳送至物件，並接收來自物件的訊息 `priority_buffer` 。

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. 在 **`protected`** 區段中，定義 `propagate_to_any_targets` 方法。

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets`方法會將位於輸入佇列前端的訊息傳送至輸出佇列，並將輸出佇列中的所有訊息傳播出去。

1. 在 **`protected`** 區段中，定義 `accept_message` 方法。

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   當目標區塊呼叫方法時 `accept_message` ，類別會將 `priority_buffer` 訊息的擁有權轉移至接受它的第一個目標區塊。 （這類似于的行為 `unbounded_buffer` ）。

1. 在 **`protected`** 區段中，定義 `reserve_message` 方法。

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`當提供的訊息識別碼與位於佇列前端的訊息識別碼相符時，類別允許目標區塊保留訊息。 換句話說，如果 `priority_buffer` 物件尚未收到額外的訊息，而且尚未傳播目前的訊息，則目標可以保留訊息。

1. 在 **`protected`** 區段中，定義 `consume_message` 方法。

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目標區塊會呼叫 `consume_message` 來傳送它所保留之訊息的擁有權。

1. 在 **`protected`** 區段中，定義 `release_message` 方法。

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目標區塊會呼叫 `release_message` 來取消其對訊息的保留。

1. 在 **`protected`** 區段中，定義 `resume_propagation` 方法。

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   在目標區塊之後，執行時間呼叫會取用 `resume_propagation` 或釋放保留的訊息。 這個方法會傳播輸出佇列中的任何訊息。

1. 在 **`protected`** 區段中，定義 `link_target_notification` 方法。

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`成員變數是由基類所定義 `source_block` 。 這個成員變數會指向目標區塊（如果有的話），其中保留位於輸出佇列前端的訊息。 `link_target_notification`當新的目標連結至物件時，執行時間會呼叫 `priority_buffer` 。 如果沒有目標持有保留，這個方法就會傳播輸出佇列中的任何訊息。

1. 在 **`private`** 區段中，定義 `propagate_priority_order` 方法。

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   這個方法會傳播輸出佇列中的所有訊息。 佇列中的每個訊息都會提供給每個目標區塊，直到其中一個目標區塊接受訊息為止。 `priority_buffer`類別會保留外寄訊息的順序。 因此，在此方法提供任何其他訊息給目標區塊之前，目標區塊必須接受輸出佇列中的第一個訊息。

1. 在 **`protected`** 區段中，定義 `propagate_message` 方法。

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`方法可讓 `priority_buffer` 類別作為訊息接收者或目標。 這個方法會接收提供的來源區塊所提供的訊息，並將該訊息插入優先順序佇列中。 然後，方法會以 `propagate_message` 非同步方式將所有輸出訊息傳送至目標區塊。

   當您呼叫[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊時，執行時間會呼叫這個方法。

1. 在 **`protected`** 區段中，定義 `send_message` 方法。

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   `send_message`方法類似 `propagate_message` 。 不過，它會同步傳送輸出訊息，而不是以非同步方式傳送。

   執行時間會在同步傳送作業期間呼叫這個方法，例如當您呼叫[concurrency：： send](reference/concurrency-namespace-functions.md#send)函式時。

`priority_buffer`類別包含許多訊息區塊類型中一般的函式多載。 某些函式多載會採用[concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器或[Concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)物件，讓訊息區塊可由特定的工作排程器管理。 其他的函數多載會接受篩選函數。 篩選函數可讓訊息區塊依據其裝載來接受或拒絕訊息。 如需訊息篩選器的詳細資訊，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。 如需工作排程器的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

因為 `priority_buffer` 類別會依優先順序排序訊息，然後再依接收訊息的順序排列，所以當您呼叫[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊時，這個類別最有用。

[[頂端](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>完整範例

下列範例顯示類別的完整定義 `priority_buffer` 。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

下列範例 `asend` 會在物件上同時執行數個和[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)作業 `priority_buffer` 。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

這個範例會產生下列範例輸出。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`類別會先依優先順序排序訊息，然後再依接收訊息的順序排列。 在此範例中，會將具有較高數值優先順序的訊息插入佇列的前方。

[[頂端](#top)]

## <a name="compiling-the-code"></a>編譯程式碼

請複製範例程式碼，並將它貼入 Visual Studio 專案中，或將類別的定義貼入名為的檔案中，然後在名為的檔案中 `priority_buffer` `priority_buffer.h` `priority_buffer.cpp` 執行下列命令，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。

**cl.exe/EHsc priority_buffer .cpp**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
