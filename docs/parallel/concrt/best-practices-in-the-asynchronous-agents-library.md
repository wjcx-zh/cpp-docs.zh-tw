---
title: 最佳做法，非同步代理程式的文件庫中 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f1b20342ad6bb64c653a211f9af2fb9e9130286
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692661"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>非同步代理程式程式庫中的最佳做法
本文件說明如何有效地運用非同步代理程式程式庫。 以行動為基礎程式設計的模型和同處理序訊息傳遞，以進行粗略的資料流程和管線工作，將會升級代理程式程式庫。  
  
 如需有關代理程式程式庫的詳細資訊，請參閱[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)。  
  
##  <a name="top"></a> 章節  
 本文件包含下列章節：  
  
- [使用隔離狀態的代理程式](#isolation)  
  
- [使用節流機制，來限制在資料管線中的訊息數目](#throttling)  
  
- [不會在資料管線中執行更細緻的工作](#fine-grained)  
  
- [不傳值方式傳遞大型訊息承載](#large-payloads)  
  
- [Shared_ptr 用於資料網路時擁有權是未定義](#ownership)  
  
##  <a name="isolation"></a> 使用隔離狀態的代理程式  
 代理程式程式庫會提供共用狀態的替代方案，可讓您透過非同步的訊息傳遞機制連接獨立的元件。 當它們隔離其內部狀態的其他元件時，非同步代理程式時最有效。 藉由隔離狀態，多個元件不通常會在共用資料。 狀態隔離，可以啟用您的應用程式延展，因為它會減少競爭情況共用記憶體。 隔離狀態也會減少死結和競爭情形的機會，因為元件不需要同步處理對共用資料的存取。  
  
 您通常隔離中代理程式狀態資料成員中的，按住`private`或`protected`的代理程式類別和訊息緩衝區使用通訊狀態變更。 下列範例所示`basic_agent`類別，衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `basic_agent`類別用來與外部元件通訊的兩個訊息的緩衝區。 一個訊息緩衝區會保存內送訊息。其他訊息緩衝區會保存外寄訊息。  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 如需有關如何定義及使用代理程式的完整範例，請參閱[逐步解說： 建立代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。  
  
 [[靠上](#top)]  
  
##  <a name="throttling"></a> 使用節流機制，來限制在資料管線中的訊息數目  
 許多訊息緩衝區類型，例如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)，可以保留無限的數量的訊息。 當訊息產生者在資料管線來傳送訊息的速度快過取用者可以處理這些訊息時，應用程式進入低記憶體或記憶體不足的狀態。 您可以使用節流機制，例如，一個號誌，來限制同時作用中，在資料管線中的訊息數目。  
  
 下列基本範例示範如何使用來限制在資料管線中的訊息數目的信號。 資料管線會使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式來模擬的作業採用至少 100 毫秒。 這個範例會定義傳送者產生訊息的速度快過取用者可以處理這些訊息，因為`semaphore`類別，讓應用程式的作用中訊息數目限制。  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore`物件限制管線來處理最多兩個訊息一次。  
  
 在此範例中生產者傳送給取用者的相對較少的訊息。 因此，此範例不示範潛在的記憶體不足或記憶體不足的狀況。 不過，這項機制時，在資料管線包含相對較高的訊息數目。  
  
 如需如何在此範例中建立信號類別所使用的詳細資訊，請參閱[How to： 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
 [[靠上](#top)]  
  
##  <a name="fine-grained"></a> 不會在資料管線中執行更細緻的工作  
 在資料管線所執行的工作時相當廣泛，代理程式程式庫便最有用。 例如，一個應用程式元件可能會從檔案或網路連線讀取資料，以及偶爾會將該資料傳送至另一個元件。 代理程式程式庫用來將訊息傳播通訊協定會有更多成本負擔比所提供的工作平行建構的訊息傳遞機制[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 因此，請確定在資料管線所執行的工作長到足以位移這項負擔。  
  
 雖然在資料管線最有效粗略其工作時，資料管線各階段可以使用 PPL 建構，例如工作群組和平行演算法來執行更細部的工作。 如需在每個處理階段所使用的細部平行處理原則的粗略資料網路的範例，請參閱[逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 [[靠上](#top)]  
  
##  <a name="large-payloads"></a> 不傳值方式傳遞大型訊息承載  

 在某些情況下，執行階段會建立從一個訊息緩衝區傳遞到另一個訊息緩衝區的每個訊息的複本。 例如， [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別提供每個目標接收到每個訊息的複本。 執行階段也會建立一份訊息資料，當您使用訊息傳遞函式，例如[concurrency:: send](reference/concurrency-namespace-functions.md#send)和[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)寫入訊息至和讀取訊息的訊息緩衝區。 雖然此機制有助於降低同時寫入至共用資料的風險，可能會導致效能不佳的記憶體時相對較大訊息裝載。  
  
 您可以使用指標，或改善記憶體效能，當您將訊息傳遞的參考具有大型的裝載。 下列範例會比較傳遞大型訊息所要傳遞至相同的訊息類型的指標值。 這個範例定義兩個代理程式類型，`producer`和`consumer`，作`message_data`物件。 這個範例會比較所需的生產者傳送數個時間`message_data`生產者代理程式傳送數個指標所需的時間讓取用者物件`message_data`給取用者的物件。  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 這個範例會產生下列輸出範例：  
  
```Output  
Using message_data...  
took 437ms.  
Using message_data*...  
took 47ms.  
```  
  
 使用指標的版本執行得更好它便不需要執行階段建立的完整複本，因為每個`message_data`從生產者傳遞到取用者的物件。  
  
 [[靠上](#top)]  
  
##  <a name="ownership"></a> Shared_ptr 用於資料網路時擁有權是未定義  
 當您透過訊息傳遞管線或網路的指標所傳送訊息時，您通常記憶體都配置給每個訊息在網路的前面，並釋放該記憶體結尾的網路。 雖然這項機制通常非常適合，但是有些的狀況中會很難或是無法使用它。 例如，請考慮包含多個終端節點之資料網路的情況。 在此情況下，沒有任何明確的位置，以釋放記憶體的訊息。  
  
 若要解決這個問題，您可以例如使用一種機制， [std:: shared_ptr](../../standard-library/shared-ptr-class.md)，可由多個元件所擁有的指標。 當最終`shared_ptr`擁有資源的物件終結時，也會釋放資源。  
  
 下列範例示範如何使用`shared_ptr`共用在多個訊息緩衝區的指標值。 此範例會連接[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)三個物件[concurrency:: call](../../parallel/concrt/reference/call-class.md)物件。 `overwrite_buffer`類別提供訊息給每個目標。 因為有結尾的資料網路資料的多個擁有者，所以這個範例會使用`shared_ptr`啟用各個`call`共用之訊息的擁有權的物件。  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 這個範例會產生下列輸出範例：  
  
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
 [並行執行階段最佳作法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [逐步解說： 建立代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [平行模式程式庫中的最佳作法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

