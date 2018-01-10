---
title: "逐步解說： 建立自訂訊息區 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ff7dd60dbb91d88377f481510ea0e213f18098a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-custom-message-block"></a>逐步解說：建立自訂訊息區
本文件說明如何建立依優先順序排序內送訊息的自訂訊息區塊類型。  
  
 雖然內建訊息區塊類型提供各種功能，您可以建立您自己的訊息區塊類型，並自訂它以符合您的應用程式的需求。 如需非同步代理程式程式庫所提供的內建訊息區塊類型的說明，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="prerequisites"></a>必要條件  
 在開始這個逐步解說之前，請閱讀下列文件：  
  
- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
##  <a name="top"></a> 章節  
 本逐步解說包含下列各節：  
  
- [設計自訂訊息區](#design)  
  
- [定義 priority_buffer 類別](#class)  
  
- [完整範例](#complete)  
  
##  <a name="design"></a>設計自訂訊息區  
 訊息區塊參與傳送和接收訊息的動作。 將訊息傳送的訊息區塊稱為*來源區塊*。 接收訊息的訊息區塊稱為*目標區塊*。 同時傳送和接收訊息的訊息區塊稱為*傳播程式區塊*。 代理程式程式庫會使用抽象類別[concurrency:: isource](../../parallel/concrt/reference/isource-class.md)來代表來源區塊和抽象類別[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)來代表目標區塊。 訊息區塊類型可做為來源衍生自`ISource`; 訊息區塊類型可做為目標衍生自`ITarget`。  
  
 雖然您可以衍生您的訊息區塊類型，直接從`ISource`和`ITarget`，代理程式程式庫會定義三個基底類別來執行許多適用於所有的訊息區塊類型，例如，處理錯誤的功能和連接在一起以並行安全的方式訊息區塊。 [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md)類別衍生自`ISource`，並將訊息傳送至其他區塊。 [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md)類別衍生自`ITarget`，從其他區塊接收訊息。 [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md)類別衍生自`ISource`和`ITarget`，將訊息傳送至其他區塊並從其他區塊接收訊息。 我們建議您使用這三個基底類別，來處理基礎結構詳細資料，您可以專注於訊息區塊的行為。  
  
 `source_block`， `target_block`，和`propagator_block`類別是針對管理連接，或連結的類型、 來源和目標區塊之間和管理訊息的處理方式的類型參數化的範本。 代理程式程式庫定義兩個可執行連結管理[concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)和[concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。 `single_link_registry`類別可讓訊息區塊至一個來源 or 連結到一個目標。 `multi_link_registry`類別可讓訊息區塊連結至多個來源或多個目標。 代理程式程式庫會定義一個類別，可執行訊息管理[concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 `ordered_message_processor`類別可讓訊息區塊處理訊息，它接收的順序。  
  
 若要進一步了解如何訊息區塊與相關聯的來源和目標，請考慮下列的範例。 此範例中顯示的宣告[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)類別。  
  
 [!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]  
  
 `transformer`類別衍生自`propagator_block`，並因此做為這兩個來源區塊和目標區塊。 它可接受類型的訊息`_Input`和傳送訊息型別的`_Output`。 `transformer`類別會指定`single_link_registry`作為任何目標區塊的連結管理員和`multi_link_registry`作為任何來源區塊的連線管理員。 因此，`transformer`物件最多可包含一個目標和無限的數量的來源。  
  

 類別衍生自`source_block`必須實作六種方法： [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets)， [accept_message](reference/source-block-class.md#accept_message)， [reserve_message](reference/source-block-class.md#reserve_message)， [consume_message](reference/source-block-class.md#consume_message)， [release_message](reference/source-block-class.md#release_message)，和[resume_propagation](reference/source-block-class.md#resume_propagation)。 類別衍生自`target_block`必須實作[propagate_message](reference/propagator-block-class.md#propagate_message)方法，而且可以選擇性地實作[send_message](reference/propagator-block-class.md#send_message)方法。 衍生自`propagator_block`其作用相當於衍生自兩者`source_block`和`target_block`。  


  
 `propagate_to_any_targets`方法是執行階段呼叫以非同步或同步方式處理傳入的訊息，並散佈任何的外寄訊息。 `accept_message`方法會呼叫接受訊息的目標區塊。 許多訊息區塊類型，例如`unbounded_buffer`，訊息只傳送給第一個目標會接收。 因此，它會傳送訊息的擁有權至目標。 其他訊息區塊類型，例如[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)，訊息提供給每個目標區塊。 因此，`overwrite_buffer`建立訊息的複本，每個目標。  
  
 `reserve_message`， `consume_message`， `release_message`，和`resume_propagation`方法可讓訊息區塊參與訊息保留項目。 目標會封鎖呼叫`reserve_message`方法時，我們將提供一則訊息，已保留供日後使用的訊息。 目標區塊保留一則訊息之後，它可以呼叫`consume_message`取用該訊息的方法或`release_message`方法來取消此保留項目。 如同`accept_message`方法時，實作`consume_message`可以傳送訊息的擁有權，或傳回訊息的複本。 目標區塊會耗用或釋放保留的訊息後，執行階段會呼叫`resume_propagation`方法。 一般而言，這個方法會繼續訊息傳播，從佇列中的下一個訊息。  
  
 執行階段呼叫`propagate_message`將以非同步方式從另一個區塊的訊息傳送到目前的方法。 `send_message`方法類似於`propagate_message`，不同之處在於它同步執行，而不是以非同步方式將訊息傳送到目標區塊。 預設實作`send_message`會拒絕所有內送訊息。 執行階段不會呼叫其中一種方法如果訊息沒有通過目標區塊相關聯的選用篩選函式。 如需訊息篩選條件的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 [[靠上](#top)]  
  
##  <a name="class"></a>定義 priority_buffer 類別  
 `priority_buffer`類別是依優先順序，再依接收訊息的順序，先排序內送訊息的自訂訊息區塊類型。 `priority_buffer`類別類似於[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)類別，因為它包含佇列的訊息，以及因為它可做為來源和目標訊息區塊，而且可以有多個來源和多個目標。 不過，`unbounded_buffer`基底訊息傳播只在它接收訊息與其來源的順序。  
  
 `priority_buffer`類別類型的訊息會接收 std::[tuple](../../standard-library/tuple-class.md)包含`PriorityType`和`Type`項目。 `PriorityType`參考型別所在的每個訊息; 優先順序`Type`指的是訊息的資料部分。 `priority_buffer`類別將傳送訊息型別的`Type`。 `priority_buffer`類別也會管理兩個訊息佇列： [std::priority_queue](../../standard-library/priority-queue-class.md)物件內送訊息和 std::[佇列](../../standard-library/queue-class.md)外寄訊息的物件。 依優先順序排序訊息時，有用`priority_buffer`物件同時接收多個訊息，或當它收到多個訊息之前的任何訊息會被取用者讀取。  
  
 除了七種方法的類別，衍生自`propagator_block`必須實作`priority_buffer`類別也會覆寫`link_target_notification`和`send_message`方法。 `priority_buffer`類別也會定義兩個公用的 helper 方法，`enqueue`和`dequeue`，和私用 helper 方法， `propagate_priority_order`。  
  
 下列程序描述如何實作`priority_buffer`類別。  
  
#### <a name="to-define-the-prioritybuffer-class"></a>若要定義 priority_buffer 類別  
  
1.  建立 c + + 標頭檔並將其命名`priority_buffer.h`。 或者，您可以使用現有的標頭檔的專案的一部分。  
  
2.  在`priority_buffer.h`，加入下列程式碼。  
  
 [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]  
  
3.  在`std`命名空間中，定義的特製化[std:: less<>](../../standard-library/less-struct.md)和[std:: less](../../standard-library/greater-struct.md)作 concurrency::[訊息](../../parallel/concrt/reference/message-class.md)物件。  
  
 [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]  
  
     `priority_buffer`類別存放區`message`中的物件`priority_queue`物件。 這些類型特製化可以讓優先順序佇列，以便排序根據其優先順序的訊息。 優先順序是第一個項目`tuple`物件。  
  
4.  在`concurrencyex`命名空間中，宣告`priority_buffer`類別。  
  
 [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]  
  
     `priority_buffer` 類別衍生自 `propagator_block`。 因此，它可以同時傳送和接收訊息。 `priority_buffer`類別可以有多個目標會接收的訊息類型的`Type`。 它也可以有多個來源的傳送類型的訊息`tuple<PriorityType, Type>`。  
  
5.  在`private`區段`priority_buffer`類別中，加入下列成員變數。  
  
 [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]  
  
     `priority_queue`物件會保存內送訊息;`queue`物件會保留外寄訊息。 A`priority_buffer`物件可以同時接收多個訊息;`critical_section`物件同步處理的輸入訊息佇列的存取。  
  
6.  在`private`區段中，定義複製建構函式和指派運算子。 這可防止`priority_queue`從所指派的物件。  
  
 [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]  
  
7.  在`public`區段中，定義通用於許多訊息區塊類型建構函式。 也定義解構函式。  
  
 [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]  
  
8.  在`public`區段中，定義方法`enqueue`和`dequeue`。 這些 helper 方法提供的替代方式將訊息傳送至與接收郵件的`priority_buffer`物件。  
  
 [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]  
  
9. 在`protected`區段中，定義`propagate_to_any_targets`方法。  
  
 [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]  
  
     `propagate_to_any_targets`方法傳送的訊息，是位於輸出佇列的輸入佇列，並散佈輸出佇列中的所有訊息。  
  
10. 在`protected`區段中，定義`accept_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]  
  
     當目標區塊呼叫`accept_message`方法，`priority_buffer`類別的訊息擁有權轉移到第一個目標區塊接受它。 (這類似於的行為`unbounded_buffer`。)  
  
11. 在`protected`區段中，定義`reserve_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]  
  
     `priority_buffer`類別允許目標區塊保留一則訊息時提供的訊息識別項符合在佇列前端的訊息識別項。 換句話說，目標可以保留訊息如果`priority_buffer`物件尚未收到額外的訊息和尚未傳播出目前的金鑰。  
  
12. 在`protected`區段中，定義`consume_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]  
  
     目標區塊呼叫`consume_message`傳送的訊息，這個名稱能保留的擁有權。  
  
13. 在`protected`區段中，定義`release_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]  
  
     目標區塊呼叫`release_message`取消其保留的訊息。  
  
14. 在`protected`區段中，定義`resume_propagation`方法。  
  
 [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]  
  
     執行階段呼叫`resume_propagation`目標區塊會耗用或釋放保留的訊息之後。 這個方法會散佈任何輸出佇列中的訊息。  
  
15. 在`protected`區段中，定義`link_target_notification`方法。  
  
 [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]  
  
     `_M_pReservedFor`成員變數由基底類別，定義`source_block`。 這個成員變數會指向目標區塊時，如果有的話，持有的保留項目是位於輸出佇列的訊息。 執行階段呼叫`link_target_notification`新目標會連結到`priority_buffer`物件。 這個方法會散佈任何位於輸出佇列，如果沒有目標持有保留的訊息。  
  
16. 在`private`區段中，定義`propagate_priority_order`方法。  
  
 [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]  
  
     這個方法會從輸出佇列的所有郵件都散佈。 佇列中的每個訊息被提供給每個目標區塊中，直到其中一個目標區塊接受該訊息。 `priority_buffer`類別會保留外寄訊息的順序。 因此，輸出佇列的第一個訊息必須接受，目標區塊由這個方法提供給目標區塊的任何其他訊息。  
  
17. 在`protected`區段中，定義`propagate_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]  
  
     `propagate_message`方法會讓`priority_buffer`類別做為訊息接收者，或設為目標。 這個方法會接收的訊息，由提供的來源區塊所提供，並且將該訊息插入至優先權佇列。 `propagate_message`方法然後以非同步方式傳送所有訊息輸出至目標區塊。  
  

     執行階段呼叫這個方法，當您呼叫[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊。  

  
18. 在`protected`區段中，定義`send_message`方法。  
  
 [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]  
  
     `send_message`方法類似於`propagate_message`。 不過它會傳送輸出訊息，以同步方式而不是以非同步的方式。  
  

     執行階段呼叫這個方法同步傳送作業期間，例如當您呼叫[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式。  
  
 `priority_buffer`類別包含常見的許多訊息區塊類型建構函式多載。 有些建構函式多載採用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)或[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件，讓訊息區塊受特定工作排程器。 其他建構函式多載會接受篩選函數。 篩選函數可讓訊息區塊接受或拒絕訊息，以根據其內容。 如需訊息篩選條件的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。 如需工作排程器的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 因為`priority_buffer`類別排序訊息依優先權然後再依接收訊息的順序，這個類別最為實用收到訊息時以非同步的方式，例如，當您呼叫[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式或當訊息區塊連接至其他訊息區塊。  
  
 [[靠上](#top)]  
  
##  <a name="complete"></a>完整範例  
 下列範例顯示的完整定義`priority_buffer`類別。  
  
 [!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]  
  
 下列範例會同時執行多`asend`和[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)作業`priority_buffer`物件。  

  
 [!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]  
  
 這個範例會產生下列輸出範例。  
  
```Output  
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36  
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24  
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12  
```  
  
 `priority_buffer`類別排序訊息先依優先權然後再由它接收到訊息的順序。 在此範例中，目標佇列的前端插入更大的數字優先順序的訊息。  
  
 [[靠上](#top)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼上的定義`priority_buffer`類別的檔案中，名為`priority_buffer.h`和測試程式的檔案中，名為`priority_buffer.cpp`，然後在 Visual Studio 中執行下列命令命令提示字元 視窗中。  
  
 **cl.exe /EHsc priority_buffer.cpp**  
  
## <a name="see-also"></a>請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
