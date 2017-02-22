---
title: "內容 | Microsoft Docs"
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
  - "內容 [並行執行階段]"
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 內容
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段中的內容的角色。 附加至排程器執行緒稱為 *執行內容*, ，或簡稱 *內容*。  [Concurrency:: wait](../Topic/wait%20Function.md) 函式和並行存取::[內容類別](../../parallel/concrt/reference/context-class.md) 讓您控制內容的行為。 使用 `wait` 暫止目前的內容，在指定時間的函式。 使用 `Context` 類別時，您需要更充分掌控內容時封鎖、 解除封鎖，並產生，或當您想要過度訂閱目前內容。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 因為工作排程器可協助您微調應用程式的效能，我們建議您開始 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md) 如果您不熟悉並行執行階段。  
  
## <a name="the-wait-function"></a>等候函式  
  [Concurrency:: wait](../Topic/wait%20Function.md) 函式以合作方式會產生指定的毫秒數的目前內容執行。 執行階段使用 yield 時間執行其他工作。 指定的時間經過之後，執行階段重新排程執行的內容。 因此， `wait` 函式可能會暫停目前的內容提供的值超過 `milliseconds` 參數。  
  
 傳遞 0 （零） `milliseconds` 參數會導致執行階段將暫停目前的內容，直到所有其他使用中的內容有機會可以執行的工作。 這可讓您產生其他所有作用中工作的工作。  
  
### <a name="example"></a>範例  
 如需範例，會使用 `wait` 函式以產生目前的內容，並因此允許其他內容中執行，請參閱 [How to︰ 使用排程群組的執行順序會影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="the-context-class"></a>內容類別  
 Concurrency::[內容類別](../../parallel/concrt/reference/context-class.md) 提供抽象的程式設計執行內容，並提供兩個重要功能︰ 能夠以合作方式封鎖、 解除封鎖及產生目前的內容，以及過度訂閱目前內容的能力。  
  
### <a name="cooperative-blocking"></a>合作式封鎖  
  `Context` 類別可讓您封鎖或產生目前的執行內容。 因為資源無法使用，無法繼續目前的內容時，封鎖或產生這種方式很有用。  
  
  [Concurrency::Context::Block](../Topic/Context::Block%20Method.md) 方法會封鎖目前的內容。 被封鎖的內容會產生其處理資源，以便讓執行階段執行其他工作。  [Concurrency::Context::Unblock](../Topic/Context::Unblock%20Method.md) 方法將會解除封鎖已封鎖的內容。  `Context::Unblock` 必須呼叫方法，從不同的內容將呼叫 `Context::Block`。 執行階段會擲回 [concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) 如果內容嘗試將自行解除封鎖。  
  
 若要以合作方式封鎖及解除封鎖內容，您通常呼叫 [concurrency::Context::CurrentContext](../Topic/Context::CurrentContext%20Method.md) 擷取變數的指標， `Context` 與目前執行緒，並將結果儲存相關聯的物件。 然後呼叫 `Context::Block` 方法來封鎖目前的內容。 更新版本中，呼叫 `Context::Unblock` 從個別的內容解除封鎖已封鎖的內容。  
  
 您必須符合呼叫的每一對 `Context::Block` 和 `Context::Unblock`。 執行階段會擲回 [concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) 時 `Context::Block` 或 `Context::Unblock` 而另一個方法呼叫不連續呼叫方法。 不過，您不需要呼叫 `Context::Block` 之前先呼叫 `Context::Unblock`。 例如，如果一個內容會呼叫 `Context::Unblock` 另一個內容呼叫之前 `Context::Block` 該內容就會針對相同的內容保持解除封鎖。  
  
  [Yield](../Topic/Context::Yield%20Method.md) 方法產生的執行，以便在執行階段可以執行其他工作，然後重新排程執行的內容。 當您呼叫 `Context::Block` 方法中，執行階段不重新排程的內容。  
  
#### <a name="example"></a>範例  
 如需範例，會使用 `Context::Block`, ，`Context::Unblock`, ，和 `Context::Yield` 方法來實作合作式信號類別，請參閱 [How to︰ 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
##### <a name="oversubscription"></a>過度訂閱  
 預設排程器會建立相同的執行緒數目，如有可用的硬體執行緒。 您可以使用 *過度訂閱* 建立額外的執行緒特定的硬體執行緒。  
  
 針對密集作業，過度訂閱通常無法調整由於帶來了額外的負荷。 不過，對於具有大量延遲的工作，比方說，讀取資料，從磁碟或網路連線、 過度訂閱可以改善某些應用程式的整體效率。  
  
> [!NOTE]
>  只從並行執行階段所建立的執行緒啟用過度訂閱。 過度訂閱有任何作用，它不執行階段 （包括主執行緒） 所建立的執行緒中呼叫時。  
  
 若要啟用過度訂閱目前內容中的，呼叫 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法 `_BeginOversubscription` 參數設定為 `true`。 當您啟用過度訂閱上並行執行階段所建立的執行緒時，它會讓執行階段建立一個額外的執行緒。 需要過度訂閱完成的所有工作] 之後，呼叫 `Context::Oversubscribe` 與 `_BeginOversubscription` 參數設定為 `false`。  
  
 您可以啟用過度訂閱目前內容中多次，但是您就必須停用它，使其相同次數。 過度訂閱也可以是巢狀。也就是使用過度訂閱的另一個工作所建立的工作可以也過度訂閱其內容。 不過，如果巢狀的工作和其父代隸屬於相同的內容中，只有最外層呼叫 `Context::Oversubscribe` 會導致建立額外的執行緒。  
  
> [!NOTE]
>  執行階段會擲回 [concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) 如果已停用過度訂閱，才能加以啟用。  
  
###### <a name="example"></a>範例  
 位移因從網路連接讀取資料的延遲使用過度訂閱的範例，請參閱 [How to︰ 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何︰ 使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [如何︰ 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [如何︰ 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

