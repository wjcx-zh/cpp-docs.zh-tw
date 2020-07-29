---
title: 同步處理資料結構
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 244aaac9bd40c83d0bbec3c360bdf7351da54baf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231659"
---
# <a name="synchronization-data-structures"></a>同步處理資料結構

並行執行階段提供數個資料結構，可讓您從多個執行緒同步存取共用資料。 當您有不常修改的共用資料時，這些資料結構會很有用。 比方說，同步處理物件（例如重要區段）會造成其他執行緒等待，直到共用資源可供使用為止。 因此，如果您使用這類物件來同步存取經常使用的資料，您的應用程式可能會失去擴充性。 [平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency：：組合](../../parallel/concrt/reference/combinable-class.md)類別，可讓您在多個執行緒或工作之間共用資源，而不需要同步處理。 如需類別的詳細資訊 `combinable` ，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="sections"></a><a name="top"></a>各節

本主題詳細說明下列非同步訊息區塊類型：

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock 和 scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a><a name="critical_section"></a>critical_section

[Concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)類別代表合作的相互排除物件，它會產生其他工作，而不是將其搶佔。 當多個執行緒需要共用資料的獨佔讀取和寫入權限時，重要區段會很有用。

`critical_section`類別是不可重新進入的。 [Concurrency：： critical_section：： lock](reference/critical-section-class.md#lock)方法會擲回[concurrency：： improper_lock](../../parallel/concrt/reference/improper-lock-class.md)類型的例外狀況（如果它是由已經擁有鎖定的執行緒所呼叫）。

### <a name="methods-and-features"></a>方法和功能

下表顯示類別所定義的重要方法 `critical_section` 。

|方法|說明|
|------------|-----------------|
|[狀](reference/critical-section-class.md#lock)|取得重要區段。 呼叫內容會封鎖，直到取得鎖定為止。|
|[try_lock](reference/critical-section-class.md#try_lock)|嘗試取得重要區段，但不會封鎖。|
|[解除鎖定](reference/critical-section-class.md#unlock)|釋放重要區段。|

[[頂端](#top)]

## <a name="reader_writer_lock"></a><a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)類別提供共用資料的安全線程讀取/寫入作業。 當多個執行緒需要共用資源的並行讀取權限，但很少寫入該共用資源時，請使用讀取器/寫入器鎖定。 此類別在任何時間都只會提供物件的一個執行緒寫入權限。

`reader_writer_lock`類別的執行效果優於 `critical_section` 類別，因為物件會取得 `critical_section` 共用資源的獨佔存取權，以防止並行讀取權限。

`critical_section`和類別一樣， `reader_writer_lock` 類別代表會產生給其他工作的合作相互排除物件，而不是將其搶佔。

當必須寫入共用資源的執行緒取得讀取器/寫入器鎖定時，其他也必須存取資源的執行緒會遭到封鎖，直到寫入器釋放鎖定為止。 `reader_writer_lock`類別是*寫入喜好*設定鎖定的範例，這是在解除封鎖等候讀取器之前，解除封鎖等候中寫入器的鎖定。

就像 `critical_section` 類別一樣， `reader_writer_lock` 類別是不可重新進入的。 如果[concurrency：： reader_writer_lock：： lock](reference/reader-writer-lock-class.md#lock)和[concurrency：： reader_writer_lock：： lock_read](reference/reader-writer-lock-class.md#lock_read)方法 `improper_lock` 是由已經擁有鎖定的執行緒所呼叫，則會擲回類型的例外狀況。

> [!NOTE]
> 因為 `reader_writer_lock` 類別是不可重新進入的，所以您無法將唯讀鎖定升級為讀取器/寫入器鎖定，或將讀取器/寫入器鎖定降級為唯讀鎖定。 執行其中一項作業會產生未指定的行為。

### <a name="methods-and-features"></a>方法和功能

下表顯示類別所定義的重要方法 `reader_writer_lock` 。

|方法|說明|
|------------|-----------------|
|[狀](reference/reader-writer-lock-class.md#lock)|取得鎖定的讀取/寫入存取權。|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|嘗試取得鎖定的讀取/寫入存取權，但不會封鎖。|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|取得鎖定的唯讀存取權。|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|嘗試取得鎖定的唯讀存取權，但不會封鎖。|
|[解除鎖定](reference/reader-writer-lock-class.md#unlock)|釋放鎖定。|

[[頂端](#top)]

## <a name="scoped_lock-and-scoped_lock_read"></a><a name="scoped_lock"></a>scoped_lock 和 scoped_lock_read

`critical_section`和 `reader_writer_lock` 類別提供的嵌套協助程式類別，可簡化處理相互排除物件的方式。 這些 helper 類別稱為*範圍鎖定*。

`critical_section`類別包含[concurrency：： critical_section：： scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)類別。 此函式會取得所提供物件的存取權 `critical_section` ; 此析構函數會釋放該物件的存取權。 `reader_writer_lock`類別包含[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別，其類似 `critical_section::scoped_lock` ，不同之處在于它會管理所提供物件的寫入權限 `reader_writer_lock` 。 `reader_writer_lock`類別也包含[concurrency：： reader_writer_lock：： scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class)類別。 這個類別會管理所提供物件的讀取權限 `reader_writer_lock` 。

限定範圍的鎖定可在您手動使用和物件時提供數個優點 `critical_section` `reader_writer_lock` 。 一般來說，您會在堆疊上配置範圍鎖定。 已設定範圍的鎖定會在終結時自動釋放其相互排除物件的存取權;因此，您不需要手動解除鎖定基礎物件。 當函數包含多個語句時，這會很有用 **`return`** 。 限定範圍的鎖定也可以協助您撰寫例外狀況安全的程式碼。 當 **`throw`** 語句導致堆疊回溯時，會呼叫任何作用中範圍鎖定的析構函式，因此一律會正確地釋放相互排除物件。

> [!NOTE]
> 當您使用 `critical_section::scoped_lock` 、 `reader_writer_lock::scoped_lock` 和類別時， `reader_writer_lock::scoped_lock_read` 請勿手動釋放基礎相互排除物件的存取權。 這可能會使執行時間處於無效狀態。

## <a name="event"></a><a name="event"></a> 事件

[Concurrency：： event](../../parallel/concrt/reference/event-class.md)類別代表其狀態可以是信號或非信號的同步處理物件。 不同于同步處理物件（例如重要區段），其目的是要保護共用資料的存取，事件會同步執行流程。

`event`當某項工作已完成另一個工作的工作時，類別會很有用。 例如，其中一個工作可能會通知另一個工作，它已從網路連線或從檔案讀取資料。

### <a name="methods-and-features"></a>方法和功能

下表顯示類別所定義的數個重要方法 `event` 。

|方法|說明|
|------------|-----------------|
|[等候](reference/event-class.md#wait)|等待事件變成信號。|
|[set](reference/event-class.md#set)|將事件設定為已發出信號的狀態。|
|[reset](reference/event-class.md#reset)|將事件設定為非信號的狀態。|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等候多個事件被通知。|

### <a name="example"></a>範例

如需顯示如何使用類別的範例 `event` ，請參閱[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[頂端](#top)]

## <a name="related-sections"></a>相關章節

[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
比較同步處理資料結構與 Windows API 所提供的行為。

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。
