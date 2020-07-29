---
title: 非同步訊息區
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 6697bdd296a3c71f03bc22986efa47dd586d5d9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217905"
---
# <a name="asynchronous-message-blocks"></a>非同步訊息區

代理程式程式庫提供數種訊息區塊類型，可讓您以執行緒安全的方式在應用程式元件之間傳播訊息。 這些訊息區塊類型通常用於各種訊息傳遞常式，例如[concurrency：： send](reference/concurrency-namespace-functions.md#send)、 [concurrency：： asend](reference/concurrency-namespace-functions.md#asend)、 [concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和[concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)。 如需代理程式程式庫所定義之訊息傳遞常式的詳細資訊，請參閱[訊息傳遞](../../parallel/concrt/message-passing-functions.md)函式。

## <a name="sections"></a><a name="top"></a>各節

本主題包含下列幾節：

- [來源和目標](#sources_and_targets)

- [訊息傳播](#propagation)

- [訊息區塊類型總覽](#overview)

- [unbounded_buffer 類別](#unbounded_buffer)

- [overwrite_buffer 類別](#overwrite_buffer)

- [single_assignment 類別](#single_assignment)

- [呼叫類別](#call)

- [轉換器類別](#transformer)

- [choice 類別](#choice)

- [聯結和 multitype_join 類別](#join)

- [timer 類別](#timer)

- [訊息篩選](#filtering)

- [訊息保留](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a>來源和目標

來源和目標是訊息傳遞的兩個重要參與者。 *來源*是指傳送訊息的通訊端點。 「*目標*」（target）指的是接收訊息的通訊端點。 您可以將來源視為您從中讀取的端點，並將目標視為您寫入的端點。 應用程式會將來源和目標連接在一起，以形成*訊息網路*。

代理程式程式庫會使用兩個抽象類別來代表來源和目標： [concurrency：： ISource](../../parallel/concrt/reference/isource-class.md)和[Concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md)。 當做來源衍生自的訊息區塊類型 `ISource` ; 作為目標的訊息區塊類型會衍生自 `ITarget` 。 作為來源和目標的訊息區塊類型會衍生自 `ISource` 和 `ITarget` 。

[[頂端](#top)]

## <a name="message-propagation"></a><a name="propagation"></a>訊息傳播

*訊息傳播*是指將訊息從一個元件傳送至另一個元件的動作。 當訊息區塊提供訊息時，它可以接受、拒絕或延後該訊息。 每個訊息區塊類型都會以不同的方式來儲存和傳輸訊息。 例如，類別會 `unbounded_buffer` 儲存不限數目的訊息，類別會 `overwrite_buffer` 一次儲存單一訊息，而轉換器類別則會儲存每個訊息的變更版本。 本檔稍後會更詳細地說明這些訊息區塊類型。

當訊息區塊接受訊息時，它可以選擇性地執行工作，而且如果訊息區塊是來源，請將產生的訊息傳遞給網路的另一個成員。 訊息區塊可以使用篩選函數來拒絕不想接收的訊息。 在本主題稍後的「[訊息篩選](#filtering)」一節中，將會更詳細地描述篩選。 延後訊息的訊息區塊可以保留該訊息，並于稍後使用。 在本主題稍後的「[訊息保留](#reservation)」一節中，將會更詳細地說明訊息保留。

代理程式程式庫可讓訊息區塊以非同步或同步方式傳遞訊息。 當您以同步方式將訊息傳遞至訊息區塊時（例如，藉由使用函式 `send` ），執行時間會封鎖目前的內容，直到目標區塊接受或拒絕訊息為止。 當您以非同步方式將訊息傳遞至訊息區塊（例如，藉由使用函式）時，執行時間會將 `asend` 訊息提供給目標，如果目標接受訊息，執行時間就會排程將訊息傳播至接收者的非同步工作。 執行時間會使用輕量工作，以合作方式傳播訊息。 如需有關輕量工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

應用程式會將來源和目標連接在一起，以形成訊息網路。 一般來說，您會連結網路並呼叫 `send` 或 `asend` ，以將資料傳遞至網路。 若要將來源訊息區塊連接到目標，請呼叫[concurrency：： ISource：： link_target](reference/isource-class.md#link_target)方法。 若要中斷來源區塊與目標的連線，請呼叫[concurrency：： ISource：： unlink_target](reference/isource-class.md#unlink_target)方法。 若要中斷來源區塊與其所有目標的連線，請呼叫[concurrency：： ISource：： unlink_targets](reference/isource-class.md#unlink_targets)方法。 當其中一個預先定義的訊息區塊類型離開範圍或被終結時，它會自動與任何目標區塊中斷連接。 某些訊息區塊類型會限制可寫入的目標最大數目。 下一節描述適用于預先定義之訊息區塊類型的限制。

[[頂端](#top)]

## <a name="overview-of-message-block-types"></a><a name="overview"></a>訊息區塊類型總覽

下表簡要說明重要訊息區塊類型的角色。

[unbounded_buffer](#unbounded_buffer)<br/>
儲存訊息的佇列。

[overwrite_buffer](#overwrite_buffer)<br/>
儲存可以多次寫入和讀取的一則訊息。

[single_assignment](#single_assignment)<br/>
儲存一則訊息，可寫入一次，並從多次讀取。

[call](#call)<br/>
會在收到訊息時執行工作。

[轉換器](#transformer)<br/>
會在收到資料時執行工作，並將該工作的結果傳送至另一個目標區塊。 `transformer`類別可以在不同的輸入和輸出類型上作用。

[choice](#choice)<br/>
從一組來源選取第一個可用的訊息。

[聯結和擁有多類型聯結](#join)<br/>
等待從一組來源接收所有訊息，然後將訊息合併為另一個訊息區塊的一個訊息。

[timer](#timer)<br/>
定期將訊息傳送至目標區塊。

這些訊息區塊類型具有不同的特性，使其適用于不同的情況。 以下是一些特性：

- *傳播類型*：訊息區塊是否做為資料的來源、資料的接收者或兩者。

- *訊息排序*：訊息區塊是否會維護傳送或接收訊息的原始順序。 每個預先定義的訊息區塊類型都會維護其傳送或接收訊息的原始順序。

- *來源計數*：訊息區塊可讀取的來源數目上限。

- [*目標計數*]：訊息區塊可寫入的目標最大數目。

下表顯示這些特性與各種訊息區塊類型之間的關聯性。

|訊息區塊類型|傳播類型（來源、目標或兩者）|訊息排序（已排序或未排序）|來源計數|目標計數|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|雙向|訂購時間|Unbounded|Unbounded|
|`overwrite_buffer`|雙向|訂購時間|Unbounded|Unbounded|
|`single_assignment`|雙向|訂購時間|Unbounded|Unbounded|
|`call`|目標|訂購時間|Unbounded|不適用|
|`transformer`|雙向|訂購時間|Unbounded|1|
|`choice`|雙向|訂購時間|10|1|
|`join`|雙向|訂購時間|Unbounded|1|
|`multitype_join`|雙向|訂購時間|10|1|
|`timer`|來源|不適用|不適用|1|

下列各節會更詳細地說明訊息區塊類型。

[[頂端](#top)]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a>unbounded_buffer 類別

[Concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)類別代表一般用途的非同步訊息結構。 這個類別會儲存可由多個來源寫入或由多個目標讀取之訊息的先進先出 (FIFO) 佇列。 當目標從物件接收訊息時 `unbounded_buffer` ，就會從訊息佇列中移除該訊息。 因此，雖然 `unbounded_buffer` 物件可以有多個目標，但只有一個目標會接收到每個訊息。 當您想要將多則訊息傳遞給其他元件，而且該元件必須接收每則訊息時，`unbounded_buffer` 類別就很有用。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `unbounded_buffer` 。 這個範例會將三個值傳送至 `unbounded_buffer` 物件，然後從相同的物件中讀取這些值。

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

這個範例會產生下列輸出：

```Output
334455
```

如需示範如何使用類別的完整範例 `unbounded_buffer` ，請參閱[如何：執行各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[頂端](#top)]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a>overwrite_buffer 類別

[Concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別與類別相似 `unbounded_buffer` ，不同之處在于 `overwrite_buffer` 物件只會儲存一個訊息。 此外，當目標從物件接收訊息時 `overwrite_buffer` ，該訊息不會從緩衝區中移除。 因此，多個目標會接收此訊息的複本。

`overwrite_buffer`當您想要將多個訊息傳遞至另一個元件，但該元件只需要最新的值時，類別會很有用。 當您想要將訊息廣播至多個元件時，這個類別也很有用。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `overwrite_buffer` 。 這個範例會將三個值傳送至 `overwrite _buffer` 物件，然後從相同的物件讀取目前的值三次。 這個範例類似于類別的範例 `unbounded_buffer` 。 不過， `overwrite_buffer` 類別只會儲存一個訊息。 此外，執行時間不會在讀取後從物件中移除訊息 `overwrite_buffer` 。

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

這個範例會產生下列輸出：

```Output
555555
```

如需示範如何使用類別的完整範例 `overwrite_buffer` ，請參閱[如何：執行各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[頂端](#top)]

## <a name="single_assignment-class"></a><a name="single_assignment"></a>single_assignment 類別

[Concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)類別與類別相似 `overwrite_buffer` ，不同之處在于 `single_assignment` 只能將物件寫入一次。 與 `overwrite_buffer` 類別相同的是，當目標從 `single_assignment` 物件收到訊息時，並不會從此物件中移除該訊息。 因此，多個目標會接收此訊息的複本。 `single_assignment`當您想要將一則訊息廣播至多個元件時，類別會很有用。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `single_assignment` 。 這個範例會將三個值傳送至 `single_assignment` 物件，然後從相同的物件讀取目前的值三次。 這個範例類似于類別的範例 `overwrite_buffer` 。 雖然 `overwrite_buffer` 和類別都會 `single_assignment` 儲存單一訊息，但類別只能 `single_assignment` 寫入一次。

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

這個範例會產生下列輸出：

```Output
333333
```

如需示範如何使用類別的完整範例 `single_assignment` ，請參閱[逐步解說：執行先期](../../parallel/concrt/walkthrough-implementing-futures.md)工作。

[[頂端](#top)]

## <a name="call-class"></a><a name="call"></a>呼叫類別

[Concurrency：： call](../../parallel/concrt/reference/call-class.md)類別的作用是在接收到資料時執行工作函式的訊息接收者。 此工作函式可以是 lambda 運算式、函式物件或函式指標。 `call`物件的行為與一般函式呼叫不同，因為它會與傳送訊息給它的其他元件平行運作。 如果 `call` 物件在收到訊息時正在執行工作，則會將該訊息新增至佇列。 每個 `call` 物件都會依接收佇列訊息的順序來處理它們。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `call` 。 這個範例會建立一個 `call` 物件，它會將接收到的每個值列印到主控台。 然後，此範例會將三個值傳送至 `call` 物件。 因為 `call` 物件會在個別的執行緒上處理訊息，所以這個範例也會使用 counter 變數和[event](../../parallel/concrt/reference/event-class.md)物件，以確保物件會在函式傳回 `call` 之前處理所有訊息 `wmain` 。

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

這個範例會產生下列輸出：

```Output
334455
```

如需顯示如何使用類別的完整範例 `call` ，請參閱[如何：將工作函式提供給呼叫和轉換器類別](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。

[[頂端](#top)]

## <a name="transformer-class"></a><a name="transformer"></a>轉換器類別

[Concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)類別可做為訊息接收者和訊息寄件者。 `transformer`類別與類別類似， `call` 因為它會在收到資料時執行使用者定義的工作函式。 不過， `transformer` 類別也會將工作函式的結果傳送給接收者物件。 就像 `call` 物件一樣， `transformer` 物件也會與傳送訊息給它的其他元件平行運作。 如果 `transformer` 物件在收到訊息時正在執行工作，則會將該訊息新增至佇列。 每個 `transformer` 物件都會依接收的連續處理其佇列訊息。

`transformer`類別會將其訊息傳送至一個目標。 如果您將函式 `_PTarget` 中的參數設定為 `NULL` ，稍後可以藉由呼叫[concurrency：： link_target](reference/source-block-class.md#link_target)方法來指定目標。

不同于代理程式程式庫所提供的所有其他非同步訊息區塊類型， `transformer` 類別可以在不同的輸入和輸出類型上採取動作。 將資料從一種類型轉換成另一種的能力，會使 `transformer` 類別成為許多並行網路中的重要元件。 此外，您可以在物件的工作函式中新增更精細的平行功能 `transformer` 。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `transformer` 。 這個範例會建立一個 `transformer` 物件，將每個輸入值乘以0.33，以便 **`int`** 產生 **`double`** 值做為輸出。 然後，此範例會從相同的物件接收轉換後的值 `transformer` ，並將其列印至主控台。

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

這個範例會產生下列輸出：

```Output
10.8914.5218.15
```

如需顯示如何使用類別的完整範例 `transformer` ，請參閱[如何：在資料管線中使用轉換器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

[[頂端](#top)]

## <a name="choice-class"></a><a name="choice"></a>choice 類別

[Concurrency：： choice](../../parallel/concrt/reference/choice-class.md)類別會從一組來源中選取第一個可用的訊息。 `choice`類別代表控制流程機制，而不是資料流程機制（[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫主題說明資料流程與控制流程之間的差異）。

當選擇物件 `WaitForMultipleObjects` 的參數設定為時，就會呼叫 WINDOWS API 函式 `bWaitAll` `FALSE` 。 不過，類別會將資料系結 `choice` 至事件本身，而不是系結至外部同步處理物件。

一般來說，您會將 `choice` 類別與[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函式一起使用，以驅動應用程式中的控制流程。 `choice`當您必須在具有不同類型的訊息緩衝區之間進行選取時，請使用類別。 `single_assignment`當您必須在具有相同類型的訊息緩衝區之間進行選取時，請使用類別。

您將來源連結至物件的順序 `choice` 很重要，因為它可以判斷要選取哪一個訊息。 例如，假設您將已包含訊息的多個訊息緩衝區連結至 `choice` 物件。 `choice`物件會從它所連結的第一個來源選取訊息。 連結所有來源之後，物件會 `choice` 保留每個來源接收訊息的順序。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `choice` 。 這個範例使用[concurrency：： make_choice](reference/concurrency-namespace-functions.md#make_choice)函式來建立可 `choice` 在三個訊息區塊中選取的物件。 然後，此範例會計算各種數量的斐波，並將每個結果儲存在不同的訊息區塊中。 然後，此範例會根據先完成的作業，將訊息列印到主控台。

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

這個範例會產生下列範例輸出：

```Output
fib35 received its value first. Result = 9227465
```

因為<sup>計算35個</sup>量值的工作不保證會先完成，所以這個範例的輸出可能會有所不同。

這個範例會使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法，以平行方式計算斐波和數列的數位。 如需的詳細資訊 `parallel_invoke` ，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

如需顯示如何使用類別的完整範例 `choice` ，請參閱[如何：在已完成的工作中選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)。

[[頂端](#top)]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a>聯結和 multitype_join 類別

[Concurrency：： join](../../parallel/concrt/reference/join-class.md)和[concurrency：： multitype_join](../../parallel/concrt/reference/multitype-join-class.md)類別可讓您等候一組來源的每個成員接收訊息。 `join`類別會在具有一般訊息類型的來源物件上運作。 `multitype_join`類別會在可能具有不同訊息類型的來源物件上運作。

從 `join` 或物件讀取 `multitype_join` 時，與呼叫 Windows API 函式（ `WaitForMultipleObjects` 當它的 `bWaitAll` 參數設定為）類似 `TRUE` 。 不過，就像 `choice` 物件一樣， `join` 和 `multitype_join` 物件會使用將資料系結至事件本身而非外部同步處理物件的事件機制。

從物件讀取會 `join` 產生 std：：[vector](../../standard-library/vector-class.md)物件。 從物件讀取會 `multitype_join` 產生 std：：[元組](../../standard-library/tuple-class.md)物件。 元素會依照對應的來源緩衝區連結至或物件的相同順序，出現在這些物件中 `join` `multitype_join` 。 由於您將來源緩衝區連結至或物件的順序 `join` `multitype_join` ，與產生的或物件中的專案順序相關聯 `vector` ，因此 `tuple` 建議您不要取消連結現有來源緩衝區與聯結。 這麼做可能會導致未指定的行為。

### <a name="greedy-versus-non-greedy-joins"></a>貪婪與非貪婪聯結

`join`和 `multitype_join` 類別支援貪婪和非貪婪聯結的概念。 在所有訊息都可供使用之前，*貪婪聯結*會接受來自每個來源的訊息，因為訊息可供使用。 *非貪婪聯結*會在兩個階段中接收訊息。 首先，非貪婪聯結會等候，直到從其每個來源提供訊息為止。 第二，在所有來源訊息可供使用之後，非貪婪聯結會嘗試保留每個訊息。 如果可以保留每則訊息，它會取用所有訊息，並將它們傳播到其目標。 否則，它會釋放或取消訊息保留，然後再次等待每個來源接收訊息。

貪婪聯結的執行效果優於非貪婪聯結，因為它們會立即接受訊息。 不過，在罕見的情況下，貪婪聯結可能會導致鎖死。 當您有多個聯結包含一個或多個共用來源物件時，請使用非貪婪聯接。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `join` 。 這個範例使用[concurrency：： make_join](reference/concurrency-namespace-functions.md#make_join)函式來建立可 `join` 從三個物件接收的物件 `single_assignment` 。 這個範例會計算各種數量的斐波，並將每個結果儲存在不同的 `single_assignment` 物件中，然後將物件保留的每個結果列印到主控台 `join` 。 這個範例類似于類別的範例 `choice` ，不同之處在于類別會 `join` 等候所有的來源訊息區塊接收訊息。

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

這個範例會產生下列輸出：

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

這個範例會使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法，以平行方式計算斐波和數列的數位。 如需的詳細資訊 `parallel_invoke` ，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

如需示範如何使用類別的完整範例 `join` ，請參閱[如何：選取已完成](../../parallel/concrt/how-to-select-among-completed-tasks.md)的工作和[逐步解說：使用聯結來避免鎖死](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

[[頂端](#top)]

## <a name="timer-class"></a><a name="timer"></a>timer 類別

Concurrency：：[timer 類別](../../parallel/concrt/reference/timer-class.md)可作為訊息來源。 `timer`物件在經過一段指定的時間之後，就會將訊息傳送至目標。 `timer`當您必須延遲傳送訊息，或想要定期傳送訊息時，類別會很有用。

`timer`類別只會將訊息傳送到一個目標。 如果您將函式 `_PTarget` 中的參數設定為 `NULL` ，稍後可以呼叫[Concurrency：： ISource：： link_target](reference/source-block-class.md#link_target)方法來指定目標。

`timer`物件可以重複或非重複。 若要建立重複的計時器，請在 **`true`** `_Repeating` 呼叫此函式時傳遞參數。 否則，請 **`false`** 針對參數傳遞， `_Repeating` 以建立非重複的計時器。 如果計時器重複，它會在每個間隔之後，將相同的訊息傳送至其目標。

代理程式程式庫會建立 `timer` 處於非啟動狀態的物件。 若要啟動計時器物件，請呼叫[concurrency：： timer：： start](reference/timer-class.md#start)方法。 若要停止 `timer` 物件，請摧毀物件或呼叫[concurrency：： timer：： stop](reference/timer-class.md#stop)方法。 若要暫停重複的計時器，請呼叫[concurrency：： timer：:p ause](reference/timer-class.md#pause)方法。

### <a name="example"></a>範例

下列範例顯示如何使用類別的基本結構 `timer` 。 此範例會使用 `timer` 和 `call` 物件來報告長時間作業的進度。

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

這個範例會產生下列範例輸出：

```Output
Computing fib(42)..................................................result is 267914296
```

如需顯示如何使用類別的完整範例 `timer` ，請參閱[如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。

[[頂端](#top)]

## <a name="message-filtering"></a><a name="filtering"></a>訊息篩選

當您建立訊息區塊物件時，可以提供*篩選函數*來判斷訊息區塊是否接受或拒絕訊息。 篩選函數是保證訊息區塊只接收特定值的實用方式。

下列範例示範如何建立 `unbounded_buffer` 使用篩選函數的物件，只接受偶數。 `unbounded_buffer`物件會拒絕奇數，因此不會將奇數傳播到其目標區塊。

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

這個範例會產生下列輸出：

```Output
0 2 4 6 8
```

篩選函數可以是 lambda 函式、函式指標或函式物件。 每個篩選函數都會採用下列其中一種形式。

```Output
bool (T)
bool (T const &)
```

若要排除不必要的資料複製，請在您有以傳值方式傳播的匯總類型時，使用第二個表單。

訊息篩選支援*資料流程*程式設計模型，其中元件會在接收資料時執行計算。 如需使用篩選函數控制訊息傳遞網路中之資料流程的範例，請參閱[如何：使用訊息區篩選](../../parallel/concrt/how-to-use-a-message-block-filter.md)、[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)和[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[頂端](#top)]

## <a name="message-reservation"></a><a name="reservation"></a>訊息保留

*訊息保留*可讓訊息區塊保留訊息以供稍後使用。 通常不會直接使用訊息保留。 不過，瞭解訊息保留可協助您進一步瞭解一些預先定義之訊息區塊類型的行為。

請考慮非貪婪和貪婪聯結。 這兩種都使用訊息保留來保留訊息以供稍後使用。 稍早所述，非貪婪聯結會在兩個階段中接收訊息。 在第一個階段中，非貪婪 `join` 物件會等候它的每個來源接收訊息。 非貪婪聯結接著會嘗試保留每個訊息。 如果可以保留每則訊息，它會取用所有訊息，並將它們傳播到其目標。 否則，它會釋放或取消訊息保留，然後再次等待每個來源接收訊息。

「貪婪聯結」也會從一些來源讀取輸入訊息，並在等候接收來自每個來源的訊息時，使用訊息保留來讀取其他訊息。 例如，假設有一個從訊息區塊和接收訊息的貪婪 `A` 聯結 `B` 。 如果貪婪聯結從 B 接收到兩個訊息，但是尚未收到來自的訊息 `A` ，則貪婪聯結會為中的第二個訊息儲存唯一的訊息識別碼 `B` 。 當貪婪聯結從收到訊息 `A` 並傳播這些訊息之後，它會使用儲存的訊息識別碼，以查看的第二個訊息 `B` 是否仍然可用。

當您執行自己的自訂訊息區塊類型時，可以使用訊息保留。 如需如何建立自訂訊息區塊類型的範例，請參閱[逐步解說：建立自訂訊息區塊](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。

[[頂端](#top)]

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)
