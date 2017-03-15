---
title: "非同步訊息區 | Microsoft Docs"
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
  - "非窮盡聯結 [並行執行階段]"
  - "非同步訊息區"
  - "窮盡聯結 [並行執行階段]"
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# 非同步訊息區
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代理程式程式庫提供數個訊息區塊類型，可讓您以執行緒安全的方式散佈應用程式元件之間的訊息。 這些訊息區塊類型通常會搭配使用的各種不同的訊息傳遞常式，例如 [concurrency:: send](../Topic/send%20Function.md), ，[concurrency:: asend](../Topic/asend%20Function.md), ，[concurrency:: receive](../Topic/receive%20Function.md), ，和 [concurrency:: try_receive](../Topic/try_receive%20Function.md)。 如需將代理程式程式庫所定義的常式之訊息的詳細資訊，請參閱 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 區段  
 此主題包括下列章節：  
  
- [來源和目標](#sources_and_targets)  
  
- [訊息傳播](#propagation)  
  
- [訊息區塊類型概觀](#overview)  
  
- [unbounded_buffer 類別](#unbounded_buffer)  
  
- [overwrite_buffer 類別](#overwrite_buffer)  
  
- [single_assignment 類別](#single_assignment)  
  
- [呼叫類別](#call)  
  
- [transformer 類別](#transformer)  
  
- [choice 類別](#choice)  
  
- [聯結和 multitype_join 類別](#join)  
  
- [timer 類別](#timer)  
  
- [訊息篩選](#filtering)  
  
- [訊息保留項目](#reservation)  
  
##  <a name="a-namesourcesandtargetsa-sources-and-targets"></a><a name="sources_and_targets"></a> 來源和目標  
 來源和目標都是訊息傳遞兩個重要的參與者。 A *來源* 是指將訊息傳送的通訊的端點。 A *目標* 是指接收訊息的通訊的端點。 您可以將為您從讀取的端點的來源和目標為您寫入的端點。 應用程式連接至表單的來源和目標一起 *通訊網路*。  
  
 代理程式程式庫會使用兩個抽象類別來代表來源和目標︰ [concurrency:: isource](../../parallel/concrt/reference/isource-class.md) 和 [concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)。 訊息區塊類型可做為來源衍生自 `ISource`; 訊息區塊類型可做為目標衍生自 `ITarget`。 訊息區塊類型可做為來源和目標衍生自兩者 `ISource` 和 `ITarget`。  
  
 [[靠上](#top)]  
  
##  <a name="a-namepropagationa-message-propagation"></a><a name="propagation"></a> 訊息傳播  
 *訊息傳播* 是指一個元件之間傳送訊息。 當訊息區塊提供訊息時，它可以接受、 拒絕或延後該訊息。 每個訊息區塊類型儲存，並將訊息傳送不同的方式。 例如， `unbounded_buffer` 類別會儲存不限的數目的訊息， `overwrite_buffer` 類別會儲存一次的單一訊息，並轉換程式類別將變更後的每個訊息版本。 在本文稍後詳細說明這些訊息區塊類型。  
  
 當訊息區塊接受訊息時，它可以選擇性地執行工作，然後訊息區塊是否為來源，將產生的訊息傳遞至另一個成員的網路。 訊息區塊可以使用 filter 函數拒絕不想接收的訊息。 稍後在本主題中，一節中詳細說明篩選 [訊息篩選](#filtering)。 延後訊息的訊息區塊可以保留該訊息，並在稍後使用它。 稍後在本主題中，一節中詳細說明訊息保留 [訊息保留](#reservation)。  
  
 代理程式程式庫可讓訊息區塊以非同步方式或以同步方式將訊息傳遞。 當您傳送訊息至訊息區塊同步執行，例如，使用 `send` 函式，執行階段封鎖目前的內容之前目標區塊接受或拒絕訊息。 當您傳送訊息至訊息區塊以非同步的方式，例如，使用 `asend` 函式，執行階段提供的訊息至目標，而且如果目標接受訊息，執行階段排程會傳播到接收端訊息的非同步工作。 執行階段會使用輕量型工作以合作方式傳播訊息。 如需輕量型工作的詳細資訊，請參閱 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 應用程式連接來源和目標共同組成通訊網路。 一般而言，連結的網路和呼叫 `send` 或 `asend` 將資料傳遞至網路。 若要將來源訊息區塊連接到目標，呼叫 [concurrency::ISource::link_target](../Topic/ISource::link_target%20Method.md) 方法。 若要將來源區塊中斷連線的目標，請呼叫 [concurrency::ISource::unlink_target](../Topic/ISource::unlink_target%20Method.md) 方法。 若要將來源區塊中斷所有目標，請呼叫 [concurrency::ISource::unlink_targets](../Topic/ISource::unlink_targets%20Method.md) 方法。 當其中一個預先定義的訊息區塊類型離開範圍或終結時，它會自動中斷連線本身的任何目標區塊。 某些訊息區塊類型限制可寫入的目標最大數目。 下一節描述的限制適用於預先定義的訊息區塊類型。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameoverviewa-overview-of-message-block-types"></a><a name="overview"></a> 訊息區塊類型概觀  
 下表簡要說明重要的訊息區塊類型的角色。  
  
 [unbounded_buffer](#unbounded_buffer)  
 儲存訊息的佇列。  
  
 [overwrite_buffer](#overwrite_buffer)  
 儲存一則訊息可以寫入和讀取多次。  
  
 [single_assignment](#single_assignment)  
 儲存一則訊息，可以多次讀取和寫入一次。  
  
 [呼叫](#call)  
 收到訊息時，會執行工作。  
  
 [轉換程式](#transformer)  
 當它接收資料，並將該工作的結果傳送至另一個目標區塊時，會執行工作。  `transformer` 類別可針對不同的輸入和輸出型別。  
  
 [選擇](#choice)  
 選取第一個可用的訊息從一組的來源。  
  
 [聯結和多類型的聯結](#join)  
 等候所有訊息會接收來自一組的來源，然後將訊息結合成一個訊息另一個訊息區塊。  
  
 [計時器](#timer)  
 傳送訊息至目標區塊，以定期間隔。  
  
 這些訊息區塊類型具有不同的特性，使它們適用於不同的情況。 以下為一些特性︰  
  
- *傳播類型*︰ 訊息區塊是否可做為來源資料、 收件者的資料，或兩者。  
  
- *訊息排序*︰ 訊息區塊是否會維護原始訂單訊息會傳送或接收。 每個預先定義的訊息區塊類型維護原始順序就會傳送或接收訊息。  
  
- *來源計數*︰ 訊息區塊可以讀取的來源的最大數目。  
  
- *目標計數*︰ 目標可以寫入訊息區塊的最大數目。  
  
 下表顯示這些特性如何與各種訊息區塊類型相關聯。  
  
|訊息區塊類型|傳播型別 （來源、 目標，或兩者）|訊息排序 （已排序或 Unordered）|來源計數|目標計數|  
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|  
|`unbounded_buffer`|兩種模式|Ordered|未繫結|未繫結|  
|`overwrite_buffer`|兩種模式|Ordered|未繫結|未繫結|  
|`single_assignment`|兩種模式|Ordered|未繫結|未繫結|  
|`call`|Target|Ordered|未繫結|不適用|  
|`transformer`|兩種模式|Ordered|未繫結|1|  
|`choice`|兩種模式|Ordered|10|1|  
|`join`|兩種模式|Ordered|未繫結|1|  
|`multitype_join`|兩種模式|Ordered|10|1|  
|`timer`|來源|不適用|不適用|1|  
  
 下列章節說明詳細的訊息區塊類型。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameunboundedbuffera-unboundedbuffer-class"></a><a name="unbounded_buffer"></a> unbounded_buffer 類別  
  [Unbounded_buffer](../Topic/unbounded_buffer%20Class.md) 類別代表一般用途的非同步傳訊結構。 這個類別會儲存可由多個來源寫入或由多個目標讀取之訊息的先進先出 (FIFO) 佇列。 當目標收到來自訊息 `unbounded_buffer` 物件，從訊息佇列中移除該訊息。 因此，雖然 `unbounded_buffer` 物件可以有多個目標，只有一個目標就會收到每個訊息。 當您想要將多則訊息傳遞給其他元件，而且該元件必須接收每則訊息時，`unbounded_buffer` 類別就很有用。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `unbounded_buffer` 類別。 這個範例會傳送三種值 `unbounded_buffer` 物件，然後從相同的物件讀取這些值。  
  
 [!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_1.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
334455  
```  
  
 如需完整範例，示範如何使用 `unbounded_buffer` 類別，請參閱 [How to︰ 實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameoverwritebuffera-overwritebuffer-class"></a><a name="overwrite_buffer"></a> overwrite_buffer 類別  
  [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 類別類似於 `unbounded_buffer` 類別，但是 `overwrite_buffer` 物件會儲存一個訊息。 此外，當目標收到來自訊息 `overwrite_buffer` 物件，該訊息不會從緩衝區移除。 因此，多個目標會接收此訊息的複本。  
  
  `overwrite_buffer` 類別就很有用，當您想要將多個訊息傳遞至另一個元件，但需要該元件的最新的值。 當您想要將訊息廣播至多個元件時，這個類別也很有用。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `overwrite_buffer` 類別。 這個範例會傳送三種值 `overwrite _buffer` 物件，然後讀取目前的值相同物件的三倍。 這個範例是類似的範例 `unbounded_buffer` 類別。 不過， `overwrite_buffer` 類別會儲存在單一訊息。 此外，執行階段不會移除從訊息 `overwrite_buffer` 之後會在讀取物件。  
  
 [!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_2.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
555555  
```  
  
 如需完整範例，示範如何使用 `overwrite_buffer` 類別，請參閱 [How to︰ 實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namesingleassignmenta-singleassignment-class"></a><a name="single_assignment"></a> single_assignment 類別  
  [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 類別類似於 `overwrite_buffer` 類別，但是 `single_assignment` 物件只能被寫入一次。 與 `overwrite_buffer` 類別相同的是，當目標從 `single_assignment` 物件收到訊息時，並不會從此物件中移除該訊息。 因此，多個目標會接收此訊息的複本。  `single_assignment` 類別就很有用，當您想要廣播至多個元件的一個訊息。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `single_assignment` 類別。 這個範例會傳送三種值 `single_assignment` 物件，然後讀取目前的值相同物件的三倍。 這個範例是類似的範例 `overwrite_buffer` 類別。 雖然同時 `overwrite_buffer` 和 `single_assignment` 類別儲存單一訊息， `single_assignment` 類別可以寫入至只執行一次。  
  
 [!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_3.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
333333  
```  
  
 如需完整範例，示範如何使用 `single_assignment` 類別，請參閱 [逐步解說︰ 實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namecalla-call-class"></a><a name="call"></a> 呼叫類別  
  [Concurrency:: call](../../parallel/concrt/reference/call-class.md) 類別是做為訊息接收者接收資料時執行工作的函式。 此工作的函式可以是 lambda 運算式、 函式物件或函式指標。 A `call` 物件的方式不同於一般函式呼叫行為因為它的作用是以平行方式將訊息傳送至其他元件。 如果 `call` 物件收到訊息時執行工作、 將該訊息新增至佇列。 每個 `call` 排入佇列的訊息已接收的順序物件的處理程序。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `call` 類別。 這個範例會建立 `call` 列印到主控台收到每個值的物件。 此範例接著會傳送三種值 `call` 物件。 因為 `call` 物件處理訊息另一個執行緒上的，此範例也會使用計數器變數和 [事件](../../parallel/concrt/reference/event-class.md) 物件，以確保 `call` 物件處理之前的所有訊息 `wmain` 函式會傳回。  
  
 [!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_4.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
334455  
```  
  
 如需完整範例，示範如何使用 `call` 類別，請參閱 [How to︰ 為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nametransformera-transformer-class"></a><a name="transformer"></a> transformer 類別  
  [Concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 類別是做為訊息接收者和做為訊息傳送者。  `transformer` 類別類似於 `call` 類別，因為它會執行使用者定義的工作函式時接收資料。 不過， `transformer` 類別也會將工作函式的結果傳送至收件者物件。 像 `call` 物件， `transformer` 物件會以平行方式將訊息傳送至其他元件。 如果 `transformer` 物件收到訊息時執行工作、 將該訊息新增至佇列。 每個 `transformer` 物件處理其排入佇列的訊息已接收的順序。  
  
  `transformer` 類別將訊息傳送至一個目標。 如果您設定 `_PTarget` 參數的建構函式中 `NULL`, ，您稍後可以藉由呼叫指定目標 [concurrency::link_target](../Topic/source_block::link_target%20Method.md) 方法。  
  
 不像所有其他非同步訊息區塊類型所提供的代理程式程式庫 `transformer` 類別可針對不同的輸入和輸出型別。 這項轉換為另一個可從一種類型的資料的能力 `transformer` 類別許多並行的網路中的主要元件。 此外，您可以新增更多更細緻的平行功能的工作函式中 `transformer` 物件。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `transformer` 類別。 這個範例會建立 `transformer` 物件乘以每個輸入 `int` 值以產生 0.33 `double` 做為輸出的值。 然後從相同接收已轉換之值的範例 `transformer` 物件，並列印到主控台。  
  
 [!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_5.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
10.8914.5218.15  
```  
  
 如需完整範例，示範如何使用 `transformer` 類別，請參閱 [How to︰ 在資料管線中的使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namechoicea-choice-class"></a><a name="choice"></a> choice 類別  
  [Concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 類別選取第一個可用的訊息從一組的來源。  `choice` 類別代表的流程控制機制，而不是資料流程機制 (主題 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md) 描述資料流程與控制流程之間的差異)。  
  
 從 [選擇物件讀取類似於呼叫 Windows API 函式 `WaitForMultipleObjects` 時有 `bWaitAll` 參數設定為 `FALSE`。 不過， `choice` 類別資料繫結至事件本身而不是外部的同步處理物件。  
  
 您通常會使用 `choice` 類別搭配 [concurrency:: receive](../Topic/receive%20Function.md) 函式來驅動應用程式中的控制流程。 使用 `choice` 類別時，您必須選取之間有不同類型的訊息緩衝區。 使用 `single_assignment` 類別時，您必須選取具有相同類型的訊息緩衝區之間。  
  
 您將連結來源的順序 `choice` 物件很重要，因為它可以判斷哪些訊息已選取。 例如，假設您將連結多個已包含訊息的訊息緩衝區的大小寫 `choice` 物件。  `choice` 物件中選取連結至第一個來源訊息。 連結的所有來源之後, `choice` 物件保留在其中每個來源接收訊息的順序。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `choice` 類別。 這個範例會使用 [concurrency::make_choice](../Topic/make_choice%20Function.md) 函式來建立 `choice` 在三個訊息區塊之間所選取的物件。 此範例會計算各種 Fibonacci 數字，並將每個結果儲存在不同的訊息區塊。 此範例再列印至主控台的訊息，根據第一次完成的作業。  
  
 [!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_6.cpp)]  
  
 這個範例會產生下列輸出的範例︰  
  
```Output  
fib35 received its value first. Result = 9227465  
```  
  
 因為計算 35 工作<sup>th</sup> Fibonacci 數字不保證會在第一時間完成，此範例的輸出會有所不同。  
  
 這個範例會使用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 演算法來計算 Fibonacci 數字，以平行方式。 如需詳細資訊 `parallel_invoke`, ，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 如需完整範例，示範如何使用 `choice` 類別，請參閱 [How to︰ 選取之間完成的工作](../../parallel/concrt/how-to-select-among-completed-tasks.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namejoina-join-and-multitypejoin-classes"></a><a name="join"></a> 聯結和 multitype_join 類別  
  [Concurrency:: join](../../parallel/concrt/reference/join-class.md) 和 [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) 類別可讓您等候的一組來源接收訊息的每個成員。  `join` 類別會具有一般的訊息類型的來源物件上。  `multitype_join` 類別會具有不同的訊息類型的來源物件上。  
  
 從讀取 `join` 或 `multitype_join` 物件類似於呼叫 Windows API 函式 `WaitForMultipleObjects` 時有 `bWaitAll` 參數設定為 `TRUE`。 不過，就像 `choice` 物件， `join` 和 `multitype_join` 物件會使用資料繫結至事件本身而不是外部的同步處理物件事件的機制。  
  
 從讀取 `join` 物件所產生的 std::[向量](../../standard-library/vector-class.md) 物件。 從讀取 `multitype_join` 物件所產生的 std::[tuple](../../standard-library/tuple-class.md) 物件。 元素會出現在這些物件會以相同順序，因為它們對應的來源緩衝區連結到 `join` 或 `multitype_join` 物件。 因為您將連結來源的順序緩衝區 `join` 或 `multitype_join` 物件有關聯的項目中所產生的順序 `vector` 或 `tuple` 物件時，我們建議您未取消連結現有的來源緩衝區透過聯結。 如此一來，可能會導致未指定的行為。  
  
### <a name="greedy-versus-non-greedy-joins"></a>窮盡與非窮盡聯結  
  `join` 和 `multitype_join` 類別支援窮盡和非窮盡聯結的概念。 A *窮盡聯結* 訊息可用，直到所有的訊息可接受來自每一個來源的訊息。 A *非窮盡聯結* 兩個階段中接收訊息。 首先，方式從每一個來源提供訊息等候非窮盡聯結。 第二，所有來源訊息都都無法使用之後，非窮盡聯結會嘗試保留每個訊息。 如果它可以保留每個訊息，它會消耗所有訊息，並將它們傳播到其目標。 否則，它會釋放，或取消時，訊息保留項目，再等候接收訊息的每個來源。  
  
 窮盡聯結執行效能優於非窮盡聯結，因為它們接受立即訊息。 不過，在極少數的情況下，窮盡聯結可能會導致死結。 當您有多個聯結，其中包含一或多個共用的來源物件時，請使用非窮盡聯結。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `join` 類別。 這個範例會使用 [concurrency::make_join](../Topic/make_join%20Function.md) 函式來建立 `join` 物件，可接收三 `single_assignment` 物件。 此範例會計算各種 Fibonacci 數字，並將每個結果儲存在不同的 `single_assignment` 物件，並再列印到主控台每個產生的 `join` 物件保存。 這個範例是類似的範例 `choice` 類別，但是 `join` 類別等候接收訊息的所有來源訊息區塊。  
  
 [!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_7.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008  
```  
  
 這個範例會使用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 演算法來計算 Fibonacci 數字，以平行方式。 如需詳細資訊 `parallel_invoke`, ，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 完整的範例，示範如何使用 `join` 類別，請參閱 [How to︰ 選取之間完成的工作](../../parallel/concrt/how-to-select-among-completed-tasks.md) 和 [逐步解說︰ 使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nametimera-timer-class"></a><a name="timer"></a> timer 類別  
 Concurrency::[timer 類別](../../parallel/concrt/reference/timer-class.md) 可做為訊息來源。 A `timer` 物件將訊息傳送到目標超過指定的一段時間之後。  `timer` 類別時，您必須延遲傳送郵件，或是您想要定期傳送訊息。  
  
  `timer` 類別將訊息傳送至一個目標。 如果您設定 `_PTarget` 參數的建構函式中 `NULL`, ，您稍後可以藉由呼叫指定目標 [concurrency::ISource::link_target](../Topic/source_block::link_target%20Method.md) 方法。  
  
 A `timer` 物件可以重複或不重複。 若要建立重複的計時器，傳遞 `true` 的 `_Repeating` 參數，當您呼叫建構函式。 否則，請傳遞 `false` 的 `_Repeating` 參數來建立非重複的計時器。 如果計時器會重複進行，它會傳送相同訊息到其目標之後每個間隔。  
  
 代理程式程式庫會建立 `timer` 處於非使用狀態的物件。 若要啟動計時器物件，呼叫 [concurrency::timer::start](../Topic/timer::start%20Method.md) 方法。 若要停止 `timer` 物件，終結物件或呼叫 [concurrency::timer::stop](../Topic/timer::stop%20Method.md) 方法。 若要暫停重複計時器，請呼叫 [concurrency::timer::pause](../Topic/timer::pause%20Method.md) 方法。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用的基本結構 `timer` 類別。 此範例會使用 `timer` 和 `call` 要報告的長時間作業進度的物件。  
  
 [!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_8.cpp)]  
  
 這個範例會產生下列輸出的範例︰  
  
```Output  
Computing fib(42)..................................................result is 267914296  
```  
  
 如需完整範例，示範如何使用 `timer` 類別，請參閱 [如何︰ 定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namefilteringa-message-filtering"></a><a name="filtering"></a> 訊息篩選  
 當您建立訊息區塊物件時，您可以提供 *filter 函數* ，判斷訊息區塊接受或拒絕訊息。 Filter 函式是保證的訊息區塊只接收特定值的實用方式。  
  
 下列範例示範如何建立 `unbounded_buffer` 用於 filter 函數只接受偶數數字的物件。  `unbounded_buffer` 物件拒絕奇數數字，並因此不會傳播至目標區塊奇數數字。  
  
 [!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_9.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
0 2 4 6 8  
```  
  
 Filter 函式可以是 lambda 函式、 函式指標或函式物件。 每個篩選條件的函式會採用下列格式之一。  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 若要消除不必要的複製的資料，使用第二個表單後才會傳播值彙總類型。  
  
 訊息篩選器支援 *資料流程* 程式設計模型，在收到資料時執行計算的元件。 用來控制訊息通過網路中的資料流量的篩選函數的範例，請參閱 [How to︰ 使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md), ，[逐步解說︰ 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), ，和 [逐步解說︰ 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namereservationa-message-reservation"></a><a name="reservation"></a> 訊息保留項目  
 *訊息保留* 可讓訊息區塊保留供日後使用的訊息。 一般而言，訊息保留不直接使用。 不過，了解訊息保留項目可協助您更了解一些預先定義的訊息區塊類型行為。  
  
 請考慮非窮盡和窮盡聯結。 這兩種使用訊息保留項目保留供日後使用的訊息。 描述更早版本，非窮盡聯結會接收訊息分成兩個階段。 在第一個階段，非窮盡 `join` 物件會等待每一個來源接收訊息。 非窮盡聯結接著會保留每個訊息的嘗試。 如果它可以保留每個訊息，它會消耗所有訊息，並將它們傳播到其目標。 否則，它會釋放，或取消時，訊息保留項目，再等候接收訊息的每個來源。  
  
 窮盡聯結，也會從各種來源讀取的輸入的訊息，使用訊息保留讀取其他訊息，它會等候每個來源接收訊息時。 例如，請考慮從訊息區塊接收訊息的窮盡聯結 `A` 和 `B`。 如果窮盡聯結兩個訊息接收自 B，但仍未收到來自訊息 `A`, ，窮盡聯結將儲存的第二個訊息的唯一訊息識別碼 `B`。 窮盡聯結收到的訊息之後 `A` 並傳播這些訊息，它會使用已儲存的訊息識別項，看看是否來自第二個訊息 `B` 仍然可用。  
  
 當您實作您自己的自訂訊息區塊類型時，您可以使用訊息保留項目。 如需如何建立自訂訊息區塊類型的範例，請參閱 [逐步解說︰ 建立自訂訊息區](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。  
  
 [[靠上](#top)]  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式庫](../../parallel/concrt/asynchronous-agents-library.md)

