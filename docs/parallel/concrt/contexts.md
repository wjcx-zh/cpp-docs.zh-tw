---
title: 內容
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: b7d1a5bbc63781e865be8053cb4365d6a8590935
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529164"
---
# <a name="contexts"></a>內容

本文件說明並行執行階段內容的角色。 附加至排程器的執行緒就所謂*執行內容*，或簡稱*內容*。 [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式和並行存取::[內容類別](../../parallel/concrt/reference/context-class.md)讓您控制內容的行為。 使用`wait`函式來暫停目前的內容指定的時間。 使用`Context`類別，在您需要更充分掌控內容時封鎖、 解除封鎖，，和產生，或當您想要過度訂閱目前的內容。

> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。

## <a name="the-wait-function"></a>Wait 函式

[Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式以合作方式會產生在指定的毫秒數的目前內容的執行。 執行階段使用的暫止時間執行其他工作。 指定的時間經過之後，執行階段重新排程執行的內容。 因此，`wait`函式可能會暫停目前的內容超過提供的值`milliseconds`參數。

傳遞 0 （零）`milliseconds`參數會導致執行階段將暫停目前的內容，直到所有其他使用中的內容有機會執行工作。 這可讓您產生所有其他作用中工作的工作。

### <a name="example"></a>範例

如需使用的範例`wait`函式以產生目前的內容，並因此可提供其他內容中執行，請參閱[如何： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="the-context-class"></a>Context 類別

並行::[內容類別](../../parallel/concrt/reference/context-class.md)提供執行內容的程式設計抽象概念，並提供兩個重要功能： 能夠以合作方式封鎖、 解除封鎖，並產生目前的內容，以及能夠過度訂閱目前的內容。

### <a name="cooperative-blocking"></a>合作式封鎖

`Context`類別可讓您封鎖或產生目前的執行內容。 無法繼續目前的內容，因為資源無法使用時，封鎖或產生非常有用。

[Concurrency::Context::Block](reference/context-class.md#block)方法會封鎖目前的內容。 已封鎖的內容會產生其處理資源，如此執行階段可以執行其他工作。 [Concurrency::Context::Unblock](reference/context-class.md#unblock)方法會解除封鎖已封鎖的內容。 `Context::Unblock`方法必須呼叫其中一個不同的內容從呼叫`Context::Block`。 執行階段會擲回[concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md)如果內容嘗試將自行解除封鎖。

若要以合作方式封鎖及解除封鎖的內容，一般都會呼叫[concurrency::Context::CurrentContext](reference/context-class.md#currentcontext)擷取的指標`Context`與目前執行緒，並將結果儲存相關聯的物件。 然後呼叫`Context::Block`方法來封鎖目前的內容。 更新版本中，呼叫`Context::Unblock`從個別的內容，若要解除封鎖已封鎖的內容。

您必須符合呼叫的每一對`Context::Block`和`Context::Unblock`。 執行階段會擲回[concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md)當`Context::Block`或`Context::Unblock`而不需要呼叫另一個方法連續呼叫方法。 不過，您就不必呼叫`Context::Block`呼叫之前`Context::Unblock`。 例如，如果一個內容呼叫`Context::Unblock`另一個內容呼叫之前`Context::Block`提供相同的內容，該內容會維持已解除封鎖。

[Concurrency](reference/context-class.md#yield)方法會產生執行，以便執行階段可以執行其他工作，然後重新排程執行的內容。 當您呼叫`Context::Block`方法中，執行階段不會重新排程的內容。

#### <a name="example"></a>範例

如需使用的範例`Context::Block`， `Context::Unblock`，並`Context::Yield`方法來實作合作式信號類別，請參閱[如何： 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

##### <a name="oversubscription"></a>過度訂閱

預設排程器會建立相同的執行緒數目，如有可用的硬體執行緒。 您可以使用*過度訂閱*來建立指定的硬體執行緒的其他執行緒。

針對密集運算作業，過度訂閱通常不會延展，因為它帶來額外的負荷。 不過，對於具有大量延遲的工作，比方說，讀取資料，從磁碟或網路連線、 過度訂閱可以改進某些應用程式的整體效率。

> [!NOTE]
>  只從並行執行階段所建立的執行緒啟用過度訂閱。 過度訂閱從不執行階段 （包括主執行緒） 所建立的執行緒呼叫時，沒有任何作用。

若要啟用過度訂閱目前內容中的，呼叫[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法`_BeginOversubscription`參數設定為**true**。 當您啟用並行執行階段所建立的執行緒上的過度訂閱時，它會導致執行階段建立一個額外的執行緒。 需要過度訂閱完成所有工作之後呼叫`Context::Oversubscribe`具有`_BeginOversubscription`參數設為**false**。

您可以啟用過度訂閱多次從目前的內容，但您就必須停用其相同次數，您將它啟用。 過度訂閱也可以是巢狀;也就是使用過度訂閱的另一個工作所建立的工作可以也過度訂閱其內容。 不過，如果巢狀的工作和其父代都屬於相同的內容中，只有最外層的呼叫來`Context::Oversubscribe`會導致其他執行緒的建立。

> [!NOTE]
>  執行階段會擲回[concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md)如果過度訂閱已停用，才能加以啟用。

###### <a name="example"></a>範例

如需使用過度訂閱位移的延遲所造成的網路連線讀取資料的範例，請參閱[如何： 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

