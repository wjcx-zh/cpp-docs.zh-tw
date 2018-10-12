---
title: 非同步訊息區 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b180b1a92defb2c29d0e54b0ecf9700dd299170
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163422"
---
# <a name="asynchronous-message-blocks"></a>非同步訊息區

代理程式庫提供數個訊息區塊類型，可讓您以安全執行緒方式散佈應用程式元件之間的訊息。 這些訊息區塊類型通常搭配各種訊息傳遞的常式，例如[concurrency:: send](reference/concurrency-namespace-functions.md#send)， [concurrency:: asend](reference/concurrency-namespace-functions.md#asend)， [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)，並[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)。 如需有關訊息傳遞所定義的代理程式庫常式的詳細資訊，請參閱[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)。

##  <a name="top"></a> 章節

此主題包括下列章節：

- [來源和目標](#sources_and_targets)

- [訊息傳播](#propagation)

- [訊息區塊類型的概觀](#overview)

- [unbounded_buffer 類別](#unbounded_buffer)

- [overwrite_buffer 類別](#overwrite_buffer)

- [single_assignment 類別](#single_assignment)

- [call 類別](#call)

- [transformer 類別](#transformer)

- [choice 類別](#choice)

- [聯結和 multitype_join 類別](#join)

- [timer 類別](#timer)

- [訊息篩選](#filtering)

- [訊息保留項目](#reservation)

##  <a name="sources_and_targets"></a> 來源和目標

來源和目標都是訊息傳遞兩個重要的參與者。 A*來源*指的是傳送訊息的通訊的端點。 A*目標*是指接收訊息的通訊的端點。 您可以將為您從讀取端點的來源和目標為端點所撰寫。 應用程式連接至表單的來源和目標放在一起*傳訊網路*。

代理程式庫會使用兩個抽象類別來代表來源和目標： [concurrency:: isource](../../parallel/concrt/reference/isource-class.md)並[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)。 訊息區塊類型可做為來源衍生自`ISource`; 訊息區塊類型可做為目標，是衍生自`ITarget`。 訊息區塊類型可做為來源和目標衍生自兩者`ISource`和`ITarget`。

[[靠上](#top)]

##  <a name="propagation"></a> 訊息傳播

*訊息傳播*是將訊息從一個元件傳送至另一個動作。 當訊息區塊提供一則訊息時，它可以接受、 拒絕或延後該訊息。 每個訊息區塊類型會儲存，並將訊息傳送不同的方式。 例如，`unbounded_buffer`類別會儲存無限的數量的訊息，`overwrite_buffer`類別會儲存一次的單一訊息，並轉換程式類別會儲存變更後的每個訊息版本。 本文件稍後的詳細說明這些訊息區塊類型。

當訊息區塊接受訊息時，它可以選擇性地執行工作，而且如果訊息區塊是來源，則將產生的訊息傳遞至網路的另一個成員。 訊息區塊可以使用篩選函數來拒絕不想接收的訊息。 篩選器會一節中的本主題稍後更詳細的說明[訊息篩選](#filtering)。 延後訊息的訊息區塊可保留該訊息，並稍後使用它。 訊息保留項目描述一節中的本主題稍後更詳細[訊息保留](#reservation)。

代理程式庫可讓訊息區塊以非同步方式，或以同步方式將訊息傳遞。 當您傳送訊息至訊息區塊以同步方式，比方說，使用`send`函式，直到目標區塊接受或拒絕訊息會執行階段封鎖目前的內容。 當您傳送訊息至訊息區塊以非同步的方式，比方說，使用`asend`函式執行階段提供的訊息至目標，以及執行階段目標接受訊息，如果排程會傳播訊息的非同步工作給接收者。 執行階段會使用輕量型工作，將訊息傳播合作方式。 如需輕量型工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

應用程式連接來源和目標一起通訊網路的表單。 一般而言，您連結的網路和呼叫`send`或`asend`將資料傳遞至網路。 若要將來源訊息區塊連接到目標，呼叫[concurrency::ISource::link_target](reference/isource-class.md#link_target)方法。 若要將來源區塊中斷連線的目標，請呼叫[concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target)方法。 若要將來源區塊中斷所有目標，請呼叫[concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets)方法。 當其中一個預先定義的訊息區塊類型離開範圍或被終結時，它會自動中斷連線本身的任何目標區塊。 某些訊息區塊類型限制可寫入的目標數目上限。 下一節會說明適用於預先定義的訊息區塊類型的限制。

[[靠上](#top)]

##  <a name="overview"></a> 訊息區塊類型的概觀

下表簡要說明重要的訊息區塊類型的角色。

[unbounded_buffer](#unbounded_buffer)<br/>
儲存訊息的佇列。

[overwrite_buffer](#overwrite_buffer)<br/>
會儲存一則訊息可以寫入且多次讀取。

[single_assignment](#single_assignment)<br/>
會儲存一則訊息可以多次讀取和寫入一次。

[呼叫](#call)<br/>
當它收到訊息時，會執行工作。

[transformer](#transformer)<br/>
當它接收資料，並將該工作的結果傳送至另一個目標區塊時，會執行工作。 `transformer`類別可針對不同的輸入和輸出類型。

[choice](#choice)<br/>
從一組來源中選取第一個可用的訊息。

[聯結和多類型的聯結](#join)<br/>
等候所有訊息從一組來源接收，然後結合其他訊息區塊一則訊息的訊息。

[timer](#timer)<br/>
定期，將訊息傳送至目標區塊。

這些訊息區塊類型有不同的特性，因此適用於不同的情況。 以下是一些特性：

- *傳播類型*： 訊息區塊是否當做資料、 接收者的資料，或兩者的來源。

- *訊息排序*： 訊息區塊是否維護訊息是傳送或接收的原始順序。 每個預先定義的訊息區塊型別可以維護其傳送或接收訊息的原始順序。

- *來源計數*： 訊息區塊可讀取的來源數目上限。

- *目標計數*： 訊息區塊可以寫入的目標數目上限。

下表顯示這些特性如何與各種訊息區塊類型相關聯。

|訊息區塊類型|傳播 （來源、 目標，或兩者） 的類型|訊息排序 （已排序或 Unordered）|來源計數|目標計數|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|兩種模式|排序|未繫結|未繫結|
|`overwrite_buffer`|兩種模式|排序|未繫結|未繫結|
|`single_assignment`|兩種模式|排序|未繫結|未繫結|
|`call`|目標|排序|未繫結|不適用|
|`transformer`|兩種模式|排序|未繫結|1|
|`choice`|兩種模式|排序|10|1|
|`join`|兩種模式|排序|未繫結|1|
|`multitype_join`|兩種模式|排序|10|1|
|`timer`|原始程式檔|不適用|不適用|1|

下列各節描述更詳細的訊息區塊類型。

[[靠上](#top)]

##  <a name="unbounded_buffer"></a> unbounded_buffer 類別

[Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)類別代表一般用途的非同步傳訊結構。 這個類別會儲存可由多個來源寫入或由多個目標讀取之訊息的先進先出 (FIFO) 佇列。 當目標收到來自訊息`unbounded_buffer`物件，從訊息佇列中移除該訊息。 因此，雖然`unbounded_buffer`物件可以有多個目標，只有一個目標會接收每則訊息。 當您想要將多則訊息傳遞給其他元件，而且該元件必須接收每則訊息時，`unbounded_buffer` 類別就很有用。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`unbounded_buffer`類別。 這個範例會傳送至三個值`unbounded_buffer`物件，然後這些值從讀回相同的物件。

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

這個範例會產生下列輸出：

```Output
334455
```

如需完整的範例，示範如何使用`unbounded_buffer`類別，請參閱[如何： 實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[靠上](#top)]

##  <a name="overwrite_buffer"></a> overwrite_buffer 類別

[Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別類似於`unbounded_buffer`類別，不同之處在於`overwrite_buffer`物件會儲存一個訊息。 此外，當目標收到的訊息時，才`overwrite_buffer`物件，該訊息不會從緩衝區移除。 因此，多個目標會接收此訊息的複本。

`overwrite_buffer`類別就很有用，當您想要將多個訊息傳遞給另一個元件，但該元件只需要最新的值。 當您想要將訊息廣播至多個元件時，這個類別也很有用。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`overwrite_buffer`類別。 這個範例會傳送至三個值`overwrite _buffer`物件，然後讀取目前的值相同物件的三次。 這個範例是類似的範例`unbounded_buffer`類別。 不過，`overwrite_buffer`類別會儲存一個訊息。 此外，執行階段不會移除從訊息`overwrite_buffer`物件之後讀取。

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

這個範例會產生下列輸出：

```Output
555555
```

如需完整的範例，示範如何使用`overwrite_buffer`類別，請參閱[如何： 實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[靠上](#top)]

##  <a name="single_assignment"></a> single_assignment 類別

[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)類別類似於`overwrite_buffer`類別，不同之處在於`single_assignment`物件只能寫入一次。 與 `overwrite_buffer` 類別相同的是，當目標從 `single_assignment` 物件收到訊息時，並不會從此物件中移除該訊息。 因此，多個目標會接收此訊息的複本。 `single_assignment`類別就很有用，當您想要一個訊息廣播到多個元件。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`single_assignment`類別。 這個範例會傳送至三個值`single_assignment`物件，然後讀取目前的值相同物件的三次。 這個範例是類似的範例`overwrite_buffer`類別。 雖然兩者`overwrite_buffer`並`single_assignment`類別會儲存為單一訊息，`single_assignment`類別可以撰寫一次。

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

這個範例會產生下列輸出：

```Output
333333
```

如需完整的範例，示範如何使用`single_assignment`類別，請參閱[逐步解說： 實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)。

[[靠上](#top)]

##  <a name="call"></a> call 類別

[Concurrency:: call](../../parallel/concrt/reference/call-class.md)類別是做為接收資料時執行工作的函式的訊息收件者。 此工作函式可以是 lambda 運算式、 函式物件或函式指標。 A`call`物件的方式不同於一般函式呼叫行為因為它會以平行方式將訊息傳送給它的其他元件。 如果`call`物件正在執行工作，當它收到訊息時，它會將該訊息加入佇列。 每個`call`物件處理序排入佇列的訊息接收它們的順序。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`call`類別。 這個範例會建立`call`列印到主控台收到每個值的物件。 範例接著會傳送至三個值`call`物件。 因為`call`物件處理個別的執行緒上的訊息，此範例也會使用的計數器變數和[事件](../../parallel/concrt/reference/event-class.md)物件，以確保`call`物件處理之前的所有訊息`wmain`函數會傳回。

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

這個範例會產生下列輸出：

```Output
334455
```

如需完整的範例，示範如何使用`call`類別，請參閱[如何： 為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。

[[靠上](#top)]

##  <a name="transformer"></a> transformer 類別

[Concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)類別是做為訊息接收者和做為訊息傳送者。 `transformer`類別類似於`call`類別，因為它會執行使用者定義的工作函式，當它收到的資料。 不過，`transformer`類別也會將工作函式的結果傳送至接收器物件。 像是`call`物件，`transformer`物件會以平行方式將訊息傳送給它的其他元件。 如果`transformer`物件正在執行工作，當它收到訊息時，它會將該訊息加入佇列。 每個`transformer`物件處理其已排入佇列中訊息所接收的順序。

`transformer`類別會將其訊息傳送至一個目標。 如果您設定`_PTarget`建構函式中的參數`NULL`，您稍後可以藉由呼叫指定的目標[concurrency::link_target](reference/source-block-class.md#link_target)方法。

不同於所有其他非同步訊息區塊類型所提供的代理程式庫，`transformer`類別可針對不同的輸入和輸出類型。 這項轉換為另一個可從一種類型的資料的能力`transformer`類別在多個並行的網路中的重要元件。 此外，您可以在這裡新增更多更細緻的平行處理功能的工作函式中`transformer`物件。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`transformer`類別。 這個範例會建立`transformer`倍數，每個輸入的物件`int`值以產生 0.33`double`做為輸出的值。 然後從相同接收已轉換之值的範例`transformer`物件並列印到主控台。

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

這個範例會產生下列輸出：

```Output
10.8914.5218.15
```

如需完整的範例，示範如何使用`transformer`類別，請參閱[如何： 在資料管線中的使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

[[靠上](#top)]

##  <a name="choice"></a> choice 類別

[Concurrency:: choice](../../parallel/concrt/reference/choice-class.md)類別選取第一個可用的訊息從一組的來源。 `choice`類別表示的控制流程機制，而不是資料流程機制 (主題[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)描述資料流程與控制流程之間的差異)。

從 選擇物件讀取類似於呼叫 Windows API 函式`WaitForMultipleObjects`有`bWaitAll`參數設為`FALSE`。 不過，`choice`類別將資料繫結至事件本身而不是外部的同步處理物件。

一般而言，您可以使用`choice`類別搭配[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式，來驅動應用程式中的控制流程。 使用`choice`類別時，您必須選取具有不同類型的訊息緩衝區。 使用`single_assignment`類別時，您必須選取具有相同類型的訊息緩衝區。

您將連結至來源的順序`choice`物件很重要，因為它可以決定要選取哪一個訊息。 例如，假設您用來連結多個已包含訊息的訊息緩衝區`choice`物件。 `choice`物件從它連結至第一個來源中選取訊息。 您將所有的來源連結之後`choice`物件保留在其中每個來源接收訊息的順序。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`choice`類別。 這個範例會使用[concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice)函式來建立`choice`在三個訊息區塊之間所選取的物件。 此範例會計算各種 Fibonacci 數字，並將每個結果儲存在不同的訊息區塊。 此範例接著列印至主控台以第一個完成的作業為基礎的訊息。

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

此範例會產生下列的範例輸出：

```Output
fib35 received its value first. Result = 9227465
```

因為工作計算 35<sup>th</sup> Fibonacci 數字不一定會先完成，此範例的輸出可能會不同。

這個範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法來計算 Fibonacci 數字，以平行方式。 如需詳細資訊`parallel_invoke`，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

如需完整的範例，示範如何使用`choice`類別，請參閱[如何： 選取在完成工作](../../parallel/concrt/how-to-select-among-completed-tasks.md)。

[[靠上](#top)]

##  <a name="join"></a> 聯結和 multitype_join 類別

[Concurrency:: join](../../parallel/concrt/reference/join-class.md)並[concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md)類別可讓您等候每個成員的一組來源接收的訊息。 `join`類別會具有一般的訊息類型的來源物件上。 `multitype_join`類別可以有不同的訊息類型的來源物件上的作用是。

從讀取`join`或是`multitype_join`物件類似於呼叫 Windows API 函式`WaitForMultipleObjects`有`bWaitAll`參數設定為`TRUE`。 不過，如同`choice`物件，`join`和`multitype_join`物件會使用資料繫結至事件本身而不是外部的同步處理物件的事件機制。

從讀取`join`物件會產生 std::[向量](../../standard-library/vector-class.md)物件。 從讀取`multitype_join`物件會產生 std::[tuple](../../standard-library/tuple-class.md)物件。 項目會出現在相同的順序中的這些物件連結至其對應的來源緩衝區`join`或`multitype_join`物件。 因為您將連結來源的順序緩衝處理至`join`或是`multitype_join`物件是在產生的項目的順序相關聯`vector`或`tuple`物件，我們建議您無法取消連結現有的來源緩衝區中聯結。 如此一來，可能會導致未指定的行為。

### <a name="greedy-versus-non-greedy-joins"></a>Greedy （窮盡) 與非窮盡聯結

`join`和`multitype_join`類別支援 greedy （窮盡） 和非窮盡聯結的概念。 A*窮盡聯結*訊息可用，直到所有的訊息可接受來自每一個來源的訊息。 A*非窮盡聯結*兩個階段中接收訊息。 首先，非窮盡聯結會等到它從每一個來源提供一則訊息。 第二，所有來源訊息可用之後，非窮盡聯結會嘗試保留每個訊息。 如果它可以保留每個訊息，它會取用所有的訊息，並將它們傳播至其目標。 否則，它會釋放，或取消，訊息保留項目，再等候接收訊息的每個來源。

窮盡聯結執行優於非窮盡聯結，因為它們會立即接受訊息。 不過，在罕見的情況下，窮盡聯結可能會導致死結。 當您有多個聯結，其中包含一或多個共用的來源物件時，請使用非窮盡聯結。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`join`類別。 這個範例會使用[concurrency::make_join](reference/concurrency-namespace-functions.md#make_join)函式來建立`join`物件接收的三種`single_assignment`物件。 此範例計算各種 Fibonacci 數字，並將每個結果儲存在不同`single_assignment`物件，以及然後列印至主控台每個結果，`join`物件保存。 這個範例是類似的範例`choice`類別，不同之處在於`join`等候接收訊息的所有來源訊息區塊的類別。

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

這個範例會產生下列輸出：

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

這個範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法來計算 Fibonacci 數字，以平行方式。 如需詳細資訊`parallel_invoke`，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

如需完整範例，示範如何使用`join`類別，請參閱[如何： 選取在完成工作](../../parallel/concrt/how-to-select-among-completed-tasks.md)並[逐步解說： 使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

[[靠上](#top)]

##  <a name="timer"></a> timer 類別

並行::[timer 類別](../../parallel/concrt/reference/timer-class.md)可做為訊息來源。 A`timer`物件將訊息傳送到目標經過一段指定的時間之後。 `timer`類別就很有用，您必須延遲傳送一則訊息，或您想要定期傳送訊息時。

`timer`類別會將其訊息傳送至一個目標。 如果您設定`_PTarget`建構函式中的參數`NULL`，您稍後可以藉由呼叫指定的目標[concurrency::ISource::link_target](reference/source-block-class.md#link_target)方法。

A`timer`物件可以重複，或非重複。 若要建立重複的計時器，傳遞 **，則為 true**如`_Repeating`當呼叫建構函式的參數。 否則，請傳遞**假**如`_Repeating`參數來建立非重複的計時器。 如果計時器會重複進行，它會傳送相同訊息到其目標在每個時間間隔之後。

代理程式庫建立`timer`處於非使用狀態的物件。 若要啟動計時器物件，呼叫[concurrency::timer::start](reference/timer-class.md#start)方法。 若要停止`timer`物件，終結的物件或呼叫[concurrency::timer::stop](reference/timer-class.md#stop)方法。 若要暫停重複的計時器，請呼叫[concurrency::timer::pause](reference/timer-class.md#pause)方法。

### <a name="example"></a>範例

下列範例示範如何使用的基本結構`timer`類別。 此範例會使用`timer`和`call`報告的長時間作業進度的物件。

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

此範例會產生下列的範例輸出：

```Output
Computing fib(42)..................................................result is 267914296
```

如需完整的範例，示範如何使用`timer`類別，請參閱[如何： 定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。

[[靠上](#top)]

##  <a name="filtering"></a> 訊息篩選

當您建立訊息區塊物件時，您可以提供*filter 函數*，判斷訊息區塊接受或拒絕訊息。 篩選函式是實用的方式，以確保該訊息區塊只接收特定值。

下列範例示範如何建立`unbounded_buffer`用以篩選函式接受只有偶數的物件。 `unbounded_buffer`物件會拒絕奇數的數字，並因此不會傳播至目標區塊的奇數。

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

這個範例會產生下列輸出：

```Output
0 2 4 6 8
```

篩選函式可以是 lambda 函式、 函式指標或函式物件。 每個篩選器函式會採用下列格式之一。

```Output
bool (T)
bool (T const &)
```

若要消除不必要的複製的資料，使用第二種形式，就會傳播值的彙總類型。

訊息篩選器支援*資料流程*程式設計模型，在收到資料時執行計算的元件。 如需使用篩選函數來控制的訊息傳遞網路中的資料的範例，請參閱[如何： 使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)，[逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)，和[逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[靠上](#top)]

##  <a name="reservation"></a> 訊息保留項目

*訊息保留*可讓訊息區塊保留訊息，以供稍後使用。 一般而言，訊息保留不直接使用。 不過，了解訊息保留項目可協助您更佳了解某些預先定義的訊息區塊類型行為。

請考慮非 greedy （窮盡） 和 greedy （窮盡） 的聯結。 這兩種都要保留以供稍後使用的訊息使用訊息保留。 描述更早版本，非窮盡聯結接收的訊息以兩個階段。 在第一個階段中，非窮盡`join`物件會等待每一個來源接收的訊息。 非窮盡聯結則會嘗試保留每個訊息。 如果它可以保留每個訊息，它會取用所有的訊息，並將它們傳播至其目標。 否則，它會釋放，或取消，訊息保留項目，再等候接收訊息的每個來源。

窮盡聯結，它也會從各種來源中讀取輸入的訊息，會使用訊息保留，等待接收之訊息的每個來源讀取額外的訊息。 例如，請考慮從訊息區塊接收訊息的 greedy （窮盡） 聯結`A`和`B`。 如果窮盡聯結從 B 接收兩則訊息，但尚未收到的訊息`A`，窮盡聯結儲存來自的第二個訊息的唯一訊息識別碼`B`。 Greedy （窮盡） 聯結在收到的訊息後`A`並傳播出這些訊息，它會使用已儲存的訊息識別項是否來自訊息的第二個`B`仍然可用。

當您實作您自己的自訂訊息區塊類型時，您可以使用訊息保留。 如需如何建立自訂訊息區塊類型的範例，請參閱 <<c0> [ 逐步解說： 建立自訂訊息區](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)

