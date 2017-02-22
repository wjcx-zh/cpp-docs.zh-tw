---
title: "逐步解說：建立自訂訊息區 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建立自訂訊息區 [並行執行階段]"
  - "自訂訊息區塊，建立 [並行執行階段]"
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# 逐步解說：建立自訂訊息區
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明如何建立依優先順序排序內送訊息的自訂訊息區塊類型。  
  
 雖然內建訊息區塊類型提供各種功能，您可以建立您自己的訊息區塊類型，並自訂它以符合您的應用程式的需求。 非同步代理程式程式庫所提供的內建訊息區塊類型的說明，請參閱 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="prerequisites"></a>必要條件  
 在開始本逐步解說之前，請參閱下列文件︰  
  
- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 區段  
 此逐步解說包含下列各節︰  
  
- [設計自訂訊息區](#design)  
  
- [定義 priority_buffer 類別](#class)  
  
- [完整的範例](#complete)  
  
##  <a name="a-namedesigna-designing-a-custom-message-block"></a><a name="design"></a> 設計自訂訊息區  
 訊息區塊參與傳送和接收訊息的動作。 將訊息傳送的訊息區塊稱為 *來源區塊*。 接收訊息的訊息區塊稱為 *目標區塊*。 同時傳送和接收訊息的訊息區塊稱為 *傳播程式區塊*。 代理程式程式庫會使用抽象類別 [concurrency:: isource](../../parallel/concrt/reference/isource-class.md) 來代表來源區塊和抽象類別 [concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md) 來代表目標區塊。 訊息區塊類型可做為來源衍生自 `ISource`; 訊息區塊類型可做為目標衍生自 `ITarget`。  
  
 雖然您可以直接從您的訊息區塊類型中衍生 `ISource` 和 `ITarget`, 、 代理程式程式庫會定義三個執行的許多功能都通用於所有的訊息區塊類型的基底類別，例如，處理錯誤和訊息的連接封鎖一起並行安全的方式。  [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) 類別衍生自 `ISource` ，並將訊息傳送至其他區塊。  [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) 類別衍生自 `ITarget` ，從其他區塊接收訊息。  [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md) 類別衍生自 `ISource` 和 `ITarget` ，將訊息傳送至其他區塊並從其他區塊接收訊息。 我們建議您使用這三個基底類別，來處理基礎結構詳細資料，以便您可以專注於訊息區塊的行為。  
  
  `source_block`, ，`target_block`, ，和 `propagator_block` 類別是在管理連接，或連結的類型、 來源和目標區塊之間和管理訊息的處理方式的型別上參數化的範本。 代理程式程式庫定義執行連結管理的兩種類型 [concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) 和 [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。  `single_link_registry` 類別可讓訊息區塊連結至一個來源或目標。  `multi_link_registry` 類別可讓訊息區塊連結至多個來源或多個目標。 此代理程式庫會定義一個可執行訊息管理類別 [concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。  `ordered_message_processor` 類別可讓訊息區塊處理訊息，它接收的順序。  
  
 若要進一步了解如何與它們的來源和目標訊息區塊，請考慮下列範例。 此範例中顯示的宣告 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 類別。  
  
 [!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_1.cpp)]  
  
  `transformer` 類別衍生自 `propagator_block`, ，並因此做為來源區塊和目標區塊。 它可接受類型的訊息 `_Input` 和傳送訊息型別的 `_Output`。  `transformer` 類別會指定 `single_link_registry` 作為任何目標區塊的連結管理員和 `multi_link_registry` 作為任何來源區塊的連線管理員。 因此， `transformer` 物件最多可包含一個目標和無限的數量的來源。  
  
 類別衍生自 `source_block` 必須實作六種方法︰ [propagate_to_any_targets](../Topic/source_block::propagate_to_any_targets%20Method.md), ，[accept_message](../Topic/source_block::accept_message%20Method.md), ，[reserve_message](../Topic/source_block::reserve_message%20Method.md), ，[consume_message](../Topic/source_block::consume_message%20Method.md), ，[release_message](../Topic/source_block::release_message%20Method.md), ，和 [resume_propagation](../Topic/source_block::resume_propagation%20Method.md)。 類別衍生自 `target_block` 必須實作 [propagate_message](../Topic/propagator_block::propagate_message%20Method.md) 方法，而且可以選擇性地實作 [send_message](../Topic/propagator_block::send_message%20Method.md) 方法。 衍生自 `propagator_block` 功能上相當於衍生自兩者 `source_block` 和 `target_block`。  
  
  `propagate_to_any_targets` 非同步或同步處理任何內送訊息，並散佈任何的外寄訊息的執行階段會呼叫方法。  `accept_message` 接受訊息的目標區塊會呼叫方法。 許多訊息區塊類型，例如 `unbounded_buffer`, ，會收到第一個目標，才能傳送訊息。 因此，它的訊息擁有權轉移給目標。 其他訊息區塊類型，例如 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), ，對每個目標區塊提供訊息。 因此， `overwrite_buffer` 針對每一個目標建立訊息的複本。  
  
  `reserve_message`, ，`consume_message`, ，`release_message`, ，和 `resume_propagation` 方法可讓訊息區塊參與訊息保留項目。 目標會封鎖呼叫 `reserve_message` 方法會提供一則訊息，且已保留供日後使用的訊息時。 目標區塊保留一則訊息之後，它可以呼叫 `consume_message` 方法，以使用該訊息或 `release_message` 方法來取消保留項目。 如同 `accept_message` 方法，執行 `consume_message` 可以傳送訊息的擁有權，或傳回訊息的複本。 目標區塊會耗用或釋放保留的訊息之後，執行階段會呼叫 `resume_propagation` 方法。 一般而言，這個方法會繼續訊息傳播，開始在佇列中的下一個訊息。  
  
 執行階段會呼叫 `propagate_message` 方法以非同步方式從另一個區塊傳送訊息至最新。  `send_message` 方法類似於 `propagate_message`, ，只不過它同步執行，而不是以非同步方式傳送訊息至目標區塊。 預設實作 `send_message` 會拒絕所有內送訊息。 執行階段不會呼叫其中一種方法如果訊息不會傳遞目標區塊相關聯的選擇性篩選函式。 如需訊息篩選條件的詳細資訊，請參閱 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameclassa-defining-the-prioritybuffer-class"></a><a name="class"></a> 定義 priority_buffer 類別  
  `priority_buffer` 類別是依優先順序，再依接收訊息的順序，先排序內送訊息的自訂訊息區塊類型。  `priority_buffer` 類別類似於 [unbounded_buffer](../Topic/unbounded_buffer%20Class.md) 類別，因為它會保存佇列的訊息，以及它做為來源和目標訊息區塊，而且可以有多個來源和多個目標。 不過， `unbounded_buffer` 基底訊息傳播只在它接收訊息與其來源的順序。  
  
  `priority_buffer` 類別會收到訊息類型的 std::[tuple](../../standard-library/tuple-class.md) ，其中包含 `PriorityType` 和 `Type` 項目。 `PriorityType` 參考型別所在的每個訊息; 優先順序 `Type` 指的是訊息的資料部分。  `priority_buffer` 類別會將訊息類型的 `Type`。  `priority_buffer` 類別也會管理兩個訊息佇列︰ [std::priority_queue](../../standard-library/priority-queue-class.md) 內送訊息的物件和 std::[佇列](../../standard-library/queue-class.md) 外寄訊息的物件。 依優先順序排序訊息時有用 `priority_buffer` 物件同時收到多個訊息，或是當它收到多個訊息取用者會讀取任何訊息之前。  
  
 除了七種方法的類別衍生自 `propagator_block` 必須實作 `priority_buffer` 類別也會覆寫 `link_target_notification` 和 `send_message` 方法。  `priority_buffer` 類別也會定義兩個公用的 helper 方法， `enqueue` 和 `dequeue`, ，以及私用 helper 方法， `propagate_priority_order`。  
  
 下列程序描述如何實作 `priority_buffer` 類別。  
  
#### <a name="to-define-the-prioritybuffer-class"></a>若要定義 priority_buffer 類別  
  
1.  建立 c + + 標頭檔，並將它 `priority_buffer.h`。 或者，您可以使用現有的標頭檔的專案的一部分。  
  
2.  在 `priority_buffer.h`, ，加入下列程式碼。  
  
 [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_2.h)]  
  
3.  在 `std` 命名空間定義的特製化 [concurrency:: message](../../standard-library/less-struct.md) 和 [std:: less](../../standard-library/greater-struct.md) 並行存取的作用::[訊息](../../parallel/concrt/reference/message-class.md) 物件。  
  
 [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_3.h)]  
  
      `priority_buffer` 類別商店 `message` 物件 `priority_queue` 物件。 這些類型特製化可讓優先順序佇列郵件根據優先順序進行排序。 優先權是第一個項目 `tuple` 物件。  
  
4.  在 `concurrencyex` 命名空間宣告 `priority_buffer` 類別。  
  
 [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_4.h)]  
  
     `priority_buffer` 類別衍生自 `propagator_block`。 因此，它可以同時傳送和接收訊息。  `priority_buffer` 類別可以有多個目標會接收訊息的型別 `Type`。 它也可以傳送訊息的類型的多個來源 `tuple<PriorityType, Type>`。  
  
5.  在 `private` 區段 `priority_buffer` 類別中，新增下列成員變數。  
  
 [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_5.h)]  
  
      `priority_queue` 物件保留的傳入訊息，而 `queue` 物件會保留外寄訊息。 A `priority_buffer` 物件可以同時得到多個訊息，而 `critical_section` 物件同步處理的輸入訊息佇列的存取。  
  
6.  在 `private` 區段中，定義複製建構函式和指派運算子。 這可防止 `priority_queue` 所指派的物件。  
  
 [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_6.h)]  
  
7.  在 `public` 區段中，定義通用於許多訊息區塊類型建構函式。 也定義解構函式。  
  
 [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_7.h)]  
  
8.  在 `public` 區段中，定義的方法 `enqueue` 和 `dequeue`。 這些 helper 方法提供替代方式來傳送和接收郵件的 `priority_buffer` 物件。  
  
 [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_8.h)]  
  
9. 在 `protected` 區段中，定義 `propagate_to_any_targets` 方法。  
  
 [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_9.h)]  
  
      `propagate_to_any_targets` 方法會將輸出佇列的輸入佇列堆疊和散佈輸出佇列中的所有訊息的訊息傳輸。  
  
10. 在 `protected` 區段中，定義 `accept_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_10.h)]  
  
     當目標區塊呼叫 `accept_message` 方法， `priority_buffer` 類別的訊息擁有權轉移至第一個目標區塊接受它。 (這與類似的行為 `unbounded_buffer`。)  
  
11. 在 `protected` 區段中，定義 `reserve_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_11.h)]  
  
      `priority_buffer` 類別允許目標區塊提供的訊息識別項符合識別碼的最前面的佇列的訊息時保留訊息。 換句話說，目標可以保留訊息如果 `priority_buffer` 物件仍未收到一則訊息，以及尚未傳播出目前的一個。  
  
12. 在 `protected` 區段中，定義 `consume_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_12.h)]  
  
     目標區塊會呼叫 `consume_message` 將它保留訊息的擁有權轉移。  
  
13. 在 `protected` 區段中，定義 `release_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_13.h)]  
  
     目標區塊會呼叫 `release_message` 取消其保留的訊息。  
  
14. 在 `protected` 區段中，定義 `resume_propagation` 方法。  
  
 [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_14.h)]  
  
     執行階段會呼叫 `resume_propagation` 目標區塊會耗用或釋放保留的訊息之後。 這個方法會散佈在輸出佇列中的任何訊息。  
  
15. 在 `protected` 區段中，定義 `link_target_notification` 方法。  
  
 [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_15.h)]  
  
      `_M_pReservedFor` 成員變數由基底類別，定義 `source_block`。 這個成員變數會指向目標區塊時，如果有的話，所保留的訊息，是位於輸出佇列的保留區。 執行階段會呼叫 `link_target_notification` 新目標會連結至 `priority_buffer` 物件。 這個方法會散佈任何如果沒有目標所保有的保留項目會在輸出佇列的訊息。  
  
16. 在 `private` 區段中，定義 `propagate_priority_order` 方法。  
  
 [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_16.h)]  
  
     這個方法會從輸出佇列的所有郵件都散佈。 每個訊息在佇列中的提供的每個目標區塊，直到其中一個目標區塊接受該訊息為止。  `priority_buffer` 類別會保留外寄訊息的順序。 因此，輸出佇列的第一個訊息必須接受目標區塊之前，這個方法會提供任何其他訊息到目標區塊。  
  
17. 在 `protected` 區段中，定義 `propagate_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_17.h)]  
  
      `propagate_message` 方法會讓 `priority_buffer` 類別做為訊息的收件者，或設為目標。 這個方法會接收由提供的來源區塊所提供，並將該訊息插入到優先順序佇列的訊息。  `propagate_message` 方法然後以非同步方式傳送所有訊息輸出至目標區塊。  
  
     執行階段會呼叫這個方法，當您呼叫 [concurrency:: asend](../Topic/asend%20Function.md) 函式或當訊息區塊連接至其他訊息區塊。  
  
18. 在 `protected` 區段中，定義 `send_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_18.h)]  
  
      `send_message` 方法類似於 `propagate_message`。 不過它會傳送輸出訊息，以同步方式而不是以非同步的方式。  
  
     執行階段會呼叫這個方法在同步傳送作業時，例如，當您呼叫 [concurrency:: send](../Topic/send%20Function.md) 函式。  
  
  `priority_buffer` 類別包含通常在很多訊息區塊類型的建構函式多載。 有些建構函式多載採用 [concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md) 或 [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md) 物件，讓訊息區塊受特定工作排程器。 其他建構函式多載會採用的篩選函數。 篩選函數可讓訊息區塊接受或拒絕根據其裝載的訊息。 如需訊息篩選條件的詳細資訊，請參閱 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。 如需 [工作排程器的詳細資訊，請參閱 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 因為 `priority_buffer` 類別依優先順序排序訊息然後再依接收訊息的順序，這個類別最為實用收到訊息時以非同步的方式，例如，當您呼叫 [concurrency:: asend](../Topic/asend%20Function.md) 函式或當訊息區塊連接至其他訊息區塊。  
  
 [[靠上](#top)]  
  
##  <a name="a-namecompletea-the-complete-example"></a><a name="complete"></a> 完整的範例  
 下列範例示範的完整定義 `priority_buffer` 類別。  
  
 [!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_19.h)]  
  
 下列範例會同時執行許多 `asend` 和 [concurrency:: receive](../Topic/receive%20Function.md) 作業 `priority_buffer` 物件。  
  
 [!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_20.cpp)]  
  
 這個範例會產生下列輸出範例。  
  
```Output  
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36  
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24  
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12  
```  
  
  `priority_buffer` 類別排序訊息先依優先權然後再由它接收到訊息的順序。 在此範例中，對佇列的前端插入更大的數字優先順序的訊息。  
  
 [[靠上](#top)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼並將它貼在 Visual Studio 專案中，或貼上的定義 `priority_buffer` 類別的檔案中，名為 `priority_buffer.h` 和測試程式的檔案中，名為 `priority_buffer.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc priority_buffer.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
