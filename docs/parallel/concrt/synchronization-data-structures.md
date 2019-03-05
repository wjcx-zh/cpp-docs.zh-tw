---
title: 同步處理資料結構
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: f9b949e7782c4b9ca302e9e623ce5f09061c39ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301879"
---
# <a name="synchronization-data-structures"></a>同步處理資料結構

並行執行階段提供許多可讓您同步處理從多個執行緒存取共用資料的資料結構。 當您共用，您不常修改的資料，這些資料結構會很有用。 同步處理物件，例如關鍵區段，會導致其他執行緒等候共用的資源可用為止。 因此，如果您使用這類物件同步處理存取經常使用的資料時，您可能會遺失延展性應用程式中。 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，可讓您共用的資源和數個執行緒或工作，而不需要同步處理。 如需詳細資訊`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

##  <a name="top"></a> 章節

本主題描述下列非同步訊息區塊類型，在 詳細資料：

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock 和 scoped_lock_read](#scoped_lock)

- [event](#event)

##  <a name="critical_section"></a> critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)類別代表其他工作，而非先佔它們的合作式互斥物件。 當多個執行緒要求獨佔讀取和共用資料的 「 寫入 」 權限，關鍵區段十分有用。

`critical_section`類別是不可重新進入。 [Concurrency::critical_section::lock](reference/critical-section-class.md#lock)方法會擲回的例外狀況型別的[concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md)如果它由已經擁有鎖定的執行緒呼叫。

### <a name="methods-and-features"></a>方法和功能

下表顯示所定義的重要方法`critical_section`類別。

|方法|描述|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|取得重要區段。 呼叫內容封鎖，直到它取得的鎖定。|
|[try_lock](reference/critical-section-class.md#try_lock)|嘗試取得重要區段，但不會封鎖。|
|[unlock](reference/critical-section-class.md#unlock)|釋放重要區段。|

[[靠上](#top)]

##  <a name="reader_writer_lock"></a> reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)類別提供對共用資料的安全執行緒的讀取/寫入作業。 當多個執行緒需要共用資源的並行讀取權限，但很少寫入該共用資源時，請使用讀取器/寫入器鎖定。 這個類別，讓只有一個執行緒寫入權限的物件在任何時間。

`reader_writer_lock`類別可以執行優於`critical_section`類別，因為`critical_section`物件取得獨佔存取權的共用資源，以防止並行的讀取權限。

像是`critical_section`類別，`reader_writer_lock`類別代表其他工作，而非先佔它們的合作式互斥物件。

當執行緒必須寫入至共用的資源取得讀取器/寫入器鎖定時，也必須存取資源的其他執行緒會遭到封鎖，直到寫入器解除鎖定。 `reader_writer_lock`類別是舉例*寫入喜好設定*鎖定，也就是它會解除封鎖等候讀取器之前，請解除封鎖等候寫入器的鎖定。

像是`critical_section`類別，`reader_writer_lock`類別是不可重新進入。 [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock)並[concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read)方法會擲回的例外狀況型別的`improper_lock`如果它們由已經擁有的執行緒呼叫鎖定。

> [!NOTE]
>  因為`reader_writer_lock`類別是不可重新進入，因此無法將唯讀鎖定升級至讀取器/寫入器鎖定，或降級成唯讀鎖定的讀取器/寫入器鎖定。 執行這些作業的其中一者，就會產生未指定的行為。

### <a name="methods-and-features"></a>方法和功能

下表顯示所定義的重要方法`reader_writer_lock`類別。

|方法|描述|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|取得對鎖定的讀取/寫入存取。|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|嘗試取得鎖定，讀取/寫入存取，但不會封鎖。|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|取得對鎖定的唯讀存取。|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|嘗試取得鎖定，唯讀存取，但不會封鎖。|
|[unlock](reference/reader-writer-lock-class.md#unlock)|釋放鎖定。|

[[靠上](#top)]

##  <a name="scoped_lock"></a> scoped_lock 和 scoped_lock_read

`critical_section`和`reader_writer_lock`類別提供簡化的方式，您使用互斥物件的巢狀的協助程式類別。 這些協助程式類別稱為*範圍鎖定*。

`critical_section`類別包含[scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)類別。 建構函式取得存取權提供`critical_section`物件，該物件的解構函式版本存取。 `reader_writer_lock`類別包含[scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別，類似於`critical_section::scoped_lock`，只不過它管理的寫入存取權提供`reader_writer_lock`物件。 `reader_writer_lock`類別也包含[2&gt;concurrency::reader_writer_lock::scoped_lock_read&lt;2](reference/reader-writer-lock-class.md#scoped_lock_read_class)類別。 此類別會管理讀取權限，以提供`reader_writer_lock`物件。

您正在使用時，已設定領域的鎖定會提供幾項優點`critical_section`和`reader_writer_lock`手動物件。 一般而言，您會配置在堆疊上的範圍的鎖定。 已設定領域的鎖定釋出其互斥物件的存取權的自動終結; 時因此，您不要以手動方式解除鎖定的基礎物件。 這是很有用，當函式包含多個`return`陳述式。 已設定領域的鎖定也可協助您撰寫例外狀況安全程式碼。 當`throw`陳述式會導致堆疊回溯，任何使用中的範圍鎖定的解構函式呼叫，並因此一定能夠正確釋放互斥物件。

> [!NOTE]
>  當您使用`critical_section::scoped_lock`， `reader_writer_lock::scoped_lock`，和`reader_writer_lock::scoped_lock_read`類別，不手動釋放存取基礎的互斥物件。 這會使執行階段處於無效狀態。

##  <a name="event"></a> 事件

[Concurrency:: event](../../parallel/concrt/reference/event-class.md)類別代表其狀態可以收到信號或未收到信號的同步處理物件。 不同於同步處理的物件，例如關鍵區段，其目的是要保護共用資料的存取權，事件同步處理工作流程的執行。

`event`一項工作已完成另一項工作的工作時，類別就很有用。 比方說，一項工作可能會通知另一項工作，它具有讀取資料，從網路連線或檔案。

### <a name="methods-and-features"></a>方法和功能

下表顯示數個重要的方法，由定義`event`類別。

|方法|描述|
|------------|-----------------|
|[wait](reference/event-class.md#wait)|等候事件變成收到訊號。|
|[set](reference/event-class.md#set)|設定為信號狀態的事件。|
|[reset](reference/event-class.md#reset)|設定為未收到信號的狀態事件。|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等候變成已收到訊號的多個事件。|

### <a name="example"></a>範例

如需範例，示範如何使用`event`類別，請參閱[Windows api 比較同步處理資料結構](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[靠上](#top)]

## <a name="related-sections"></a>相關章節

[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
比較同步處理的資料結構，以 Windows API 所提供的行為。

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。
