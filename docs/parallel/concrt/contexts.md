---
title: 內容
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 7df75ae7c1ac2b1d8c0b73ff1f1e3f2800d559b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194871"
---
# <a name="contexts"></a>內容

本檔說明並行執行階段內容的角色。 附加至排程器的執行緒稱為*執行內容*，或只是*內容*。 [Concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函數和 concurrency：：[CoNtext 類別](../../parallel/concrt/reference/context-class.md)可讓您控制內容的行為。 使用函式 `wait` 來暫止指定時間的目前內容。 `Context`當您需要進一步控制內容封鎖、解除封鎖及產生的時機，或當您想要過度訂閱目前的內容時，請使用類別。

> [!TIP]
> 並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，因此如果您不熟悉並行執行階段，建議您從[平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫開始。

## <a name="the-wait-function"></a>Wait 函式

[Concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函式會以合作方式，在指定的毫秒數內產生目前內容的執行。 執行時間會使用「產量」來執行其他工作。 經過指定的時間之後，執行時間會重新排定執行內容。 因此，此函式 `wait` 可能會暫停目前的內容，而不是提供給參數的值 `milliseconds` 。

傳遞0（零）給 `milliseconds` 參數會導致執行時間暫止目前的內容，直到所有其他使用中的內容都有機會執行工作為止。 這可讓您對所有其他作用中的工作產生一個工作。

### <a name="example"></a>範例

如需使用函式 `wait` 來產生目前內容的範例，因此允許其他內容執行，請參閱[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="the-context-class"></a>CoNtext 類別

Concurrency：：[CoNtext 類別](../../parallel/concrt/reference/context-class.md)提供執行內容的程式設計抽象概念，並提供兩項重要功能：能夠以合作方式封鎖、解除封鎖及產生目前內容，以及過度訂閱目前內容的能力。

### <a name="cooperative-blocking"></a>合作式封鎖

`Context`類別可讓您封鎖或產生目前的執行內容。 當目前的內容無法繼續，因為資源無法使用時，封鎖或產生會很有用。

[Concurrency：： CoNtext：： Block](reference/context-class.md#block)方法會封鎖目前的內容。 封鎖的內容會產生其處理資源，讓執行時間可以執行其他工作。 [Concurrency：： CoNtext：：解除](reference/context-class.md#unblock)封鎖方法會取消封鎖已封鎖的內容。 `Context::Unblock`方法必須從不同于呼叫的內容呼叫 `Context::Block` 。 如果內容嘗試解除封鎖本身，則執行時間會擲回[concurrency：： coNtext_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) 。

若要以合作方式封鎖和解除封鎖內容，您通常會呼叫[concurrency：： coNtext：： CurrentCoNtext](reference/context-class.md#currentcontext)來取出 `Context` 與目前線程相關聯之物件的指標，並儲存結果。 接著，您可以呼叫 `Context::Block` 方法來封鎖目前的內容。 之後， `Context::Unblock` 從個別的內容呼叫，以解除封鎖已封鎖的內容。

您必須將每一對的呼叫與和進行比對 `Context::Block` `Context::Unblock` 。 當或方法連續呼叫時，如果沒有對其他方法的相符呼叫，執行時間就會擲回[concurrency：： coNtext_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) `Context::Block` `Context::Unblock` 。 不過，在呼叫之前，您不需要呼叫 `Context::Block` `Context::Unblock` 。 例如，如果某個內容 `Context::Unblock` 在另一個內容呼叫 `Context::Block` 相同內容之前呼叫，該內容會保持解除封鎖。

[Concurrency：： CoNtext：： Yield](reference/context-class.md#yield)方法會產生執行，讓執行時間可以執行其他工作，然後重新排程要執行的內容。 當您呼叫 `Context::Block` 方法時，執行時間不會重新排定內容。

#### <a name="example"></a>範例

如需使用 `Context::Block` 、 `Context::Unblock` 和 `Context::Yield` 方法來執行合作信號類別的範例，請參閱[如何：使用內容類別來執行合作的信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

##### <a name="oversubscription"></a>過度訂閱

預設排程器會建立與可用硬體執行緒相同的執行緒數目。 您可以使用*超額訂閱*，為指定的硬體執行緒建立額外的執行緒。

對於需要大量運算的作業，過度訂閱通常不會進行調整，因為這會造成額外的負擔。 不過，對於具有大量延遲的工作，例如從磁片或網路連線讀取資料，超額訂閱可以改善某些應用程式的整體效率。

> [!NOTE]
> 只從並行執行階段所建立的執行緒啟用過度訂閱。 當過度訂閱是從執行時間（包括主執行緒）所建立的執行緒呼叫時，不會有任何作用。

若要在目前的內容中啟用過度訂閱，請呼叫[concurrency：： coNtext：：超額](reference/context-class.md#oversubscribe)方法，並將 `_BeginOversubscription` 參數設定為 **`true`** 。 當您在並行執行階段所建立的執行緒上啟用過度訂閱時，會導致執行時間建立一個額外的執行緒。 在所有需要過度訂閱的工作完成之後，請呼叫， `Context::Oversubscribe` 並將 `_BeginOversubscription` 參數設定為 **`false`** 。

您可以從目前的內容多次啟用超額訂閱，但您必須停用它的相同次數。 超額訂閱也可以嵌套;也就是說，另一項使用過度訂閱的工作所建立的工作，也可以過度訂閱其內容。 不過，如果嵌套的工作及其父系都屬於相同的內容，則只有最外層的呼叫 `Context::Oversubscribe` 會導致建立額外的執行緒。

> [!NOTE]
> 如果已停用過度訂閱，則執行時間會擲回[concurrency：： invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) 。

###### <a name="example"></a>範例

如需使用超額訂閱來抵銷從網路連線讀取資料所造成延遲的範例，請參閱[如何：使用超額訂閱來抵銷延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[如何：使用內容類別來執行合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[如何：使用超額訂閱來位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
