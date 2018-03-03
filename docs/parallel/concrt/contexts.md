---
title: "內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01ec145de3c41aeb30bdd308794d9f8d90a3f3e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="contexts"></a>內容

本文件說明並行執行階段內容的角色。 附加至排程器執行緒稱為*執行內容*，或簡稱*內容*。 [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式和 concurrency::[內容類別](../../parallel/concrt/reference/context-class.md)讓您控制內容的行為。 使用`wait`暫止目前的內容，在指定時間的函式。 使用`Context`類別時，您需要更充分掌控內容時封鎖、 解除封鎖，以及產生，或當您想要過度訂閱目前內容。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，我們建議您開始[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)如果您是新的並行執行階段。  
  
## <a name="the-wait-function"></a>等候函式  

 [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式以合作方式會產生指定的毫秒數的目前內容執行。 執行階段使用 yield 時間執行其他工作。 經過指定的時間之後，執行階段會重新排定執行的內容。 因此，`wait`函式可能會暫停目前的內容超過提供的值`milliseconds`參數。  
  
 傳遞 0 （零），以進行`milliseconds`參數會使執行階段將暫停目前的內容，直到所有其他使用中的內容會有機會執行工作。 這可讓您產生其他作用中的所有工作的工作。  
  
### <a name="example"></a>範例  
 如需範例，會使用`wait`函式，產生目前的內容，並因此允許其他內容中執行，請參閱[How to： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="the-context-class"></a>Context 類別  
 Concurrency::[內容類別](../../parallel/concrt/reference/context-class.md)提供抽象的程式設計執行內容及提供兩個重要的功能： 能夠以合作方式封鎖、 解除封鎖，並產生目前內容中，而且能夠過度訂閱目前內容。  
  
### <a name="cooperative-blocking"></a>合作式封鎖  
 `Context`類別可讓您封鎖或產生目前的執行內容。 因為資源無法使用，無法繼續目前的內容時，封鎖或產生這種方式很有用。  
  

 [Concurrency::Context::Block](reference/context-class.md#block)方法會封鎖目前的內容。 已封鎖的內容，讓執行階段可以執行其他工作，會產生其處理資源。 [Concurrency::Context::Unblock](reference/context-class.md#unblock)方法會解除封鎖已封鎖的內容。 `Context::Unblock`方法必須從不同的內容呼叫的呼叫`Context::Block`。 執行階段會擲回[concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md)如果內容嘗試將自行解除封鎖。  
  
 若要以合作方式封鎖及解除封鎖的內容，您通常呼叫[concurrency::Context::CurrentContext](reference/context-class.md#currentcontext)擷取指標`Context`與目前執行緒，並儲存結果相關聯的物件。 然後呼叫`Context::Block`方法來封鎖目前的內容。 更新版本中，呼叫`Context::Unblock`從個別的內容，若要解除封鎖已封鎖的內容。  
  
 您必須符合呼叫的每個配對`Context::Block`和`Context::Unblock`。 執行階段會擲回[concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md)時`Context::Block`或`Context::Unblock`而沒有其他方法比對呼叫連續呼叫方法。 不過，您不需要呼叫`Context::Block`之前先呼叫`Context::Unblock`。 例如，如果一個內容呼叫`Context::Unblock`另一個內容呼叫之前`Context::Block`針對相同的內容，該內容會維持已解除封鎖。  
  
 [Yield](reference/context-class.md#yield)方法可產生執行使執行階段得以執行其他工作，然後重新排程要執行的內容。 當您呼叫`Context::Block`方法，執行階段不重新排程的內容。  

  
#### <a name="example"></a>範例  
 如需範例，會使用`Context::Block`， `Context::Unblock`，和`Context::Yield`方法來實作合作式信號的類別，請參閱[How to： 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
##### <a name="oversubscription"></a>過度訂閱  
 沒有可用的硬體執行緒將預設排程器會建立相同的執行緒數目。 您可以使用*過度訂閱*來建立特定的硬體執行緒的其他執行緒。  
  
 針對密集運算作業，過度訂閱通常不會延展，因為它帶來額外的負荷。 不過，有大量的延遲的工作，例如，讀取資料，從磁碟或網路連線、 過度訂閱可以改善整體效率的某些應用程式。  
  
> [!NOTE]
>  只從並行執行階段所建立的執行緒啟用過度訂閱。 過度訂閱沒有任何作用，它不執行階段 （包括主執行緒） 所建立的執行緒從呼叫時。  
  
 若要啟用過度訂閱目前內容中的，呼叫[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法`_BeginOversubscription`參數設定為`true`。 當您啟用過度訂閱由並行執行階段所建立的執行緒上時，會導致執行階段建立一個額外的執行緒。 在需要完成過度訂閱的所有工作之後, 呼叫`Context::Oversubscribe`與`_BeginOversubscription`參數設定為`false`。  

  
 您可以啟用過度訂閱目前內容中多次，但是您就必須停用它，使其相同次數。 過度訂閱也可以巢狀。也就是由另一個工作使用過度訂閱建立的工作可能也會過度訂閱其內容。 不過，如果巢狀的工作和其父代屬於相同的內容中，只有最外層呼叫`Context::Oversubscribe`會導致建立其他的執行緒。  
  
> [!NOTE]
>  執行階段會擲回[concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md)過度訂閱已停用，才能加以啟用。  
  
###### <a name="example"></a>範例  
 如需使用過度訂閱位移的延遲所造成的網路連線讀取資料的範例，請參閱[How to： 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何： 使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [如何： 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

