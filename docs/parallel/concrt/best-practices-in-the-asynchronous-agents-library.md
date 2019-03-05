---
title: 非同步代理程式程式庫中的最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: c61393957a63895a9ecbdaaae8d83a5fbd710de3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266415"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>非同步代理程式程式庫中的最佳做法

本文件說明如何有效地使用非同步代理程式程式庫。 以行動為基礎的程式設計模型 」 和 「 同處理序訊息傳遞進行粗略的資料流程和管線工作，會將升級代理程式庫。

如需有關代理程式庫的詳細資訊，請參閱 < [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)。

##  <a name="top"></a> 章節

本文件包含下列章節：

- [使用代理程式來隔離狀態](#isolation)

- [使用節流的機制來限制資料管線中的訊息數目](#throttling)

- [不會在資料管線中執行更細緻的工作](#fine-grained)

- [請勿將大型訊息承載傳遞值](#large-payloads)

- [使用中的資料網路時擁有權是未定義的 shared_ptr](#ownership)

##  <a name="isolation"></a> 使用代理程式來隔離狀態

代理程式庫會提供共用狀態的替代方案，讓您透過非同步的訊息傳遞機制連接獨立的元件。 當他們找出其他元件從其內部狀態，非同步代理程式是最有效。 藉由隔離狀態，多個元件不通常會套用共用資料。 狀態隔離，可以讓您的應用程式調整，因為它會減少共用記憶體競爭情況。 狀態的隔離也可降低死結和競爭情形的機會，因為元件不需要同步處理共用資料的存取權。

您通常隔離在代理程式的狀態保存在資料成員`private`或`protected`agent 類別並利用訊息緩衝區來傳達狀態變更的區段。 下列範例所示`basic_agent`類別，衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `basic_agent`類別用來與外部元件通訊的兩個訊息的緩衝區。 一個訊息緩衝區會保存內送訊息;其他訊息緩衝區會保留外寄訊息。

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

如需有關如何定義及使用代理程式的完整範例，請參閱[逐步解說：建立代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。

[[靠上](#top)]

##  <a name="throttling"></a> 使用節流的機制來限制資料管線中的訊息數目

許多的訊息緩衝區型別，例如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)，可以保留無限的數量的訊息。 當訊息產生者的資料管線來傳送訊息的速度超出取用者可以處理這些訊息時，應用程式進入記憶體不足或記憶體不足的狀態。 您可以使用節流的機制，比方說，號誌，來限制同時作用中的資料管線的訊息數目。

下列基本範例會示範如何使用信號，以限制的資料管線中的訊息數目。 資料管線會使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式以模擬需要至少 100 毫秒的作業。 這個範例會定義傳送者產生訊息的速度超出取用者可以處理這些訊息，因為`semaphore`類別，以讓應用程式限制的作用中訊息數目。

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore`物件限制管線來處理最多兩個訊息一次。

在此範例中的產生者會將相對較少的訊息傳送至取用者。 因此，此範例不示範可能的記憶體太少或記憶體不足的狀況。 不過，這項機制時，資料管線中包含的訊息數量相對高。

如需如何建立號誌類別，可在此範例的詳細資訊，請參閱[How to:使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

[[靠上](#top)]

##  <a name="fine-grained"></a> 不會在資料管線中執行更細緻的工作

資料管線所執行的工作相當廣泛時，代理程式庫是最有用。 比方說，一個應用程式元件可能會從檔案或網路連線讀取資料，以及偶爾會將該資料傳送至另一個元件。 若要將訊息傳播的代理程式庫使用的通訊協定會造成有更多的額外負荷比所提供的工作平行建構的訊息傳遞機制[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 因此，請確定資料管線所執行的工作是夠長，這個額外負荷。

雖然資料管線是最有效的粗略其工作時，資料管線各階段可以使用 PPL 建構，例如工作群組和平行演算法來執行更細部的工作。 如需在每個處理階段所使用的細部平行處理原則的廣泛的資料網路的範例，請參閱[逐步解說：建立映像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[靠上](#top)]

##  <a name="large-payloads"></a> 請勿將大型訊息承載傳遞值

在某些情況下，執行階段會建立一份每則訊息，從一個訊息緩衝區傳遞到另一個訊息緩衝區。 例如， [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別提供了一份每則訊息，它會接收到其目標。 執行階段也會建立一份訊息資料，當您使用訊息傳遞函式，例如[concurrency:: send](reference/concurrency-namespace-functions.md#send)並[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)來寫入訊息和讀取訊息的訊息緩衝區。 雖然這項機制可協助降低同時寫入至共用資料的風險，它可能會導致不佳的記憶體內部效能相對較大訊息承載時。

您可以使用指標或參考，當您將訊息傳遞，改善記憶體效能有大型承載。 下列範例會比較傳遞大型訊息，將指標傳遞至相同的訊息類型的值。 此範例會定義兩個代理程式類型`producer`並`consumer`，作`message_data`物件。 這個範例會比較所需的傳送數個產生者的時間`message_data`取用者時所需的產生者代理程式傳送數個指向物件`message_data`給取用者的物件。

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

此範例會產生下列的範例輸出：

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

因為它不需要執行階段建立的完整複本，所以會使用指標的版本執行得更好每個`message_data`從生產者傳遞到取用者的物件。

[[靠上](#top)]

##  <a name="ownership"></a> 使用中的資料網路時擁有權是未定義的 shared_ptr

當您透過訊息傳遞管線或網路的指標所傳送的訊息時，您通常每個訊息的網路配置的記憶體，並釋放該記憶體，結尾的網路。 雖然這項機制經常運作良好，但是有它很難或無法使用它。 例如，請考慮包含多個終端節點之資料網路的情況。 在此情況下，沒有任何明確的位置，以釋放記憶體的訊息。

若要解決這個問題，您可以比方說，使用一種機制， [std:: shared_ptr](../../standard-library/shared-ptr-class.md)，可讓多個元件所擁有的指標。 當最終`shared_ptr`擁有資源的物件終結時，也會釋放資源。

下列範例示範如何使用`shared_ptr`共用在多個訊息緩衝區的指標值。 此範例會連接[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)物件到三[concurrency:: call](../../parallel/concrt/reference/call-class.md)物件。 `overwrite_buffer`類別提供訊息給其目標。 因為有多個擁有者的資料結尾的資料網路，所以此範例會使用`shared_ptr`若要啟用每個`call`共用擁有權之訊息的物件。

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

此範例會產生下列的範例輸出：

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>另請參閱

[並行執行階段最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[逐步解說：建立代理程式型的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[平行模式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
