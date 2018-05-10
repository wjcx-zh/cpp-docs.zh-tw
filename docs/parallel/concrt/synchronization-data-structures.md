---
title: 同步處理資料結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f64acda5fe11cae3a40e4affc403ebb61d876de
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="synchronization-data-structures"></a>同步處理資料結構
並行執行階段提供許多可讓您從多個執行緒進行同步存取共用資料的資料結構。 當您共用不常修改的資料時，這些資料結構是很有用。 同步處理物件，例如關鍵區段，會造成其他執行緒等候，直到有可用的共用的資源。 因此，如果您使用這類物件，以同步存取經常使用的資料，您可以在應用程式中遺失延展性。 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，可讓您以共用資源在數個執行緒或工作，而不需要同步處理。 如需有關`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="top"></a> 章節  
 本主題描述下列非同步訊息區塊類型，在詳細資料：  
  
-   [critical_section](#critical_section)  
  
-   [reader_writer_lock](#reader_writer_lock)  
  
-   [scoped_lock 和 scoped_lock_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a> critical_section  
 [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)類別代表其他工作而非讓給它們的合作式互斥物件。 當多個執行緒需要獨佔的讀取和寫入存取共用資料，則關鍵區段會很有用。  

 `critical_section`類別是不可重新進入。 [Concurrency::critical_section::lock](reference/critical-section-class.md#lock)方法會擲回的例外狀況型別的[concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md)如果它由已經擁有鎖定的執行緒呼叫。  


  
### <a name="methods-and-features"></a>方法與功能  
 下表顯示所定義的重要方法`critical_section`類別。  
  
|方法|描述|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|取得重要區段。 呼叫內容封鎖，直到它取得的鎖定。|  
|[try_lock](reference/critical-section-class.md#try_lock)|嘗試取得重要區段，但不會封鎖。|  
|[unlock](reference/critical-section-class.md#unlock)|釋放重要區段。|  
  
 [[靠上](#top)]  
  
##  <a name="reader_writer_lock"></a> reader_writer_lock  
 [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)類別會提供對共用資料的安全執行緒的讀取/寫入作業。 當多個執行緒需要共用資源的並行讀取權限，但很少寫入該共用資源時，請使用讀取器/寫入器鎖定。 這個類別讓物件在任何時間只能有一個執行緒寫入存取。  
  
 `reader_writer_lock`類別可以執行優於`critical_section`類別，因為`critical_section`物件取得獨佔存取共用資源，以防止並行讀取權限。  
  
 像`critical_section`類別`reader_writer_lock`類別代表其他工作而非讓給它們的合作式互斥物件。  
  
 當執行緒必須寫入至共用的資源取得讀取器/寫入器鎖定時，也必須存取資源的其他執行緒會遭到封鎖，直到寫入器會釋放鎖定為止。 `reader_writer_lock`類別是一個範例*寫入喜好設定*鎖定，而這是一種會等候寫入器的解除封鎖之前它會解除封鎖等候讀取器的鎖定。  
  
 像`critical_section`類別`reader_writer_lock`類別是不可重新進入。 [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock)和[concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read)方法會擲回的例外狀況型別的`improper_lock`如果執行緒已經擁有呼叫鎖定。  


  
> [!NOTE]
>  因為`reader_writer_lock`類別是不可重新進入，因此無法讀取器/寫入器鎖定升級唯讀鎖定或降級為唯讀狀態的鎖定的讀取器/寫入器鎖定。 執行這些作業任一，會產生未指定的行為。  
  
### <a name="methods-and-features"></a>方法與功能  
 下表顯示所定義的重要方法`reader_writer_lock`類別。  
  
|方法|描述|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|取得鎖定的讀取/寫入存取。|  
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|嘗試取得鎖定、 讀取/寫入權限，但不會封鎖。|  
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|取得鎖定的唯讀存取。|  
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|嘗試取得鎖定，唯讀存取，但不會封鎖。|  
|[unlock](reference/reader-writer-lock-class.md#unlock)|釋放鎖定。|  
  
 [[靠上](#top)]  
  
##  <a name="scoped_lock"></a> scoped_lock 和 scoped_lock_read  
 `critical_section`和`reader_writer_lock`類別提供巢狀的 helper 類別來簡化您使用互斥物件的方式。 這些 helper 類別稱為*範圍鎖定*。  
  
 `critical_section`類別包含[concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)類別。 建構函式會取得以提供存取`critical_section`物件，該物件的解構函式版本存取。 `reader_writer_lock`類別包含[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)類別，類似於`critical_section::scoped_lock`，不同之處在於它管理的寫入存取權提供`reader_writer_lock`物件。 `reader_writer_lock`類別也包含[concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class)類別。 這個類別會管理讀取權限，以提供`reader_writer_lock`物件。  

  
 已設定領域的鎖定會提供幾個優點，當您正在使用`critical_section`和`reader_writer_lock`手動物件。 一般而言，您會配置在堆疊上的已設定領域的鎖定。 已設定領域的鎖定釋出其互斥物件的存取權的自動終結時。因此，您不要以手動方式解除鎖定的基礎物件。 這適用於函式包含多個`return`陳述式。 已設定領域的鎖定也可協助您撰寫例外狀況安全程式碼。 當`throw`陳述式會導致堆疊回溯，任何已設定領域的使用中鎖定的解構函式呼叫，因此一定會正確地釋放互斥物件。  
  
> [!NOTE]
>  當您使用`critical_section::scoped_lock`， `reader_writer_lock::scoped_lock`，和`reader_writer_lock::scoped_lock_read`類別沒有手動釋放基礎互斥物件的存取權。 這可以讓執行階段處於無效狀態。  
  
##  <a name="event"></a> 事件  
 [Concurrency:: event](../../parallel/concrt/reference/event-class.md)類別代表其狀態可以收到訊號或未收到訊號的同步處理物件。 不同於同步處理物件，例如關鍵區段，其目的是為了保護共用資料的存取權，事件同步處理工作流程的執行。  
  
 `event`類別就很有用，當一個工作已完成另一項工作的工作。 例如，一個工作可能會發出信號給另一項工作，它有網路連線 或從檔案讀取資料。  
  
### <a name="methods-and-features"></a>方法與功能  
 下表顯示數個重要的方法所定義的`event`類別。  
  
|方法|描述|  
|------------|-----------------|  
|[等候](reference/event-class.md#wait)|等待事件發出訊號。|  
|[set](reference/event-class.md#set)|將事件設定為收到信號狀態。|  
|[reset](reference/event-class.md#reset)|設定為未收到信號狀態的事件。|  
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等候發出訊號的多個事件。|  

  
### <a name="example"></a>範例  
 如需範例，示範如何使用`event`類別，請參閱[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 [[靠上](#top)]  
  
## <a name="related-sections"></a>相關章節  
 [比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 比較同步處理資料結構，以 Windows API 所提供的行為。  
  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)  
 說明並行執行階段，它可簡化平行程式設計，並包含相關主題的連結。

