---
title: "同步處理資料結構 | Microsoft Docs"
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
  - "同步處理資料結構"
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# 同步處理資料結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

並行執行階段會提供許多資料結構，可讓您同步處理多個執行緒的共用資料存取權。  當您擁有不常修改的共用資料時，這些資料結構就很有用。  同步處理物件 \(例如，關鍵區段\) 會導致其他執行緒等候直到共用資源可用為止。  因此，如果您使用這類物件來同步處理經常使用之資料的存取權，可能會喪失應用程式的延展性。  [平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 提供了 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 類別，讓您不需要同步處理，即可在數個執行緒或工作之間共用資源。  如需 `combinable` 類別的詳細資訊，請參閱 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="top"></a> 章節  
 本主題將詳細描述下列非同步訊息區類型：  
  
-   [critical\_section](#critical_section)  
  
-   [reader\_writer\_lock](#reader_writer_lock)  
  
-   [scoped\_lock 和 scoped\_lock\_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a> critical\_section  
 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 類別代表讓給其他工作而非佔用它們的合作式互斥物件。  當多個執行緒需要共用資料的獨佔讀取和寫入存取權時，關鍵區段就很有用。  
  
 `critical_section` 類別是不可重新進入的。  如果 [concurrency::critical\_section::lock](../Topic/critical_section::lock%20Method.md) 方法是由已經擁有鎖定的執行緒所呼叫，它就會擲回 [concurrency::improper\_lock](../../parallel/concrt/reference/improper-lock-class.md) 型別的例外狀況。  
  
### 方法和功能  
 下表列出 `critical_section` 類別所定義的重要方法。  
  
|方法|說明|  
|--------|--------|  
|[鎖定](../Topic/critical_section::lock%20Method.md)|取得關鍵區段。  呼叫內容會封鎖，直到它取得鎖定為止。|  
|[try\_lock](../Topic/critical_section::try_lock%20Method.md)|嘗試取得關鍵區段，但是不封鎖。|  
|[unlock](../Topic/critical_section::unlock%20Method.md)|釋放關鍵區段。|  
  
 \[[上方](#top)\]  
  
##  <a name="reader_writer_lock"></a> reader\_writer\_lock  
 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 類別會提供執行緒安全的讀取\/寫入作業給共用資料。  當多個執行緒需要共用資源的並行讀取存取權，但是很少寫入該共用資源時，請使用讀取器\/寫入器鎖定。  這個類別一次只會提供物件的寫入存取權給一個執行緒。  
  
 `reader_writer_lock` 類別的執行效能可能比 `critical_section` 類別要好，因為 `critical_section` 物件會取得共用資源的獨佔存取權，因而避免並行讀取存取權。  
  
 與 `critical_section` 類別相同的是，`reader_writer_lock` 類別代表讓渡給其他工作而非佔用它們的合作式互斥物件。  
  
 當某個必須寫入共用資源的執行緒取得讀取器\/寫入器鎖定時，其他也必須存取該資源的執行緒就會被封鎖，直到寫入器釋放鎖定為止。  `reader_writer_lock` 類別是「*寫入偏好設定*」\(Write\-Preference\) 鎖定的範例，這種鎖定會先解除封鎖等候中的寫入器，然後再解除封鎖等候中的讀取器。  
  
 與 `critical_section` 類別相同的是，`reader_writer_lock` 類別是不可重新進入的。  如果 [concurrency::reader\_writer\_lock::lock](../Topic/reader_writer_lock::lock%20Method.md) 和 [concurrency::reader\_writer\_lock::lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md) 方法是由已經擁有鎖定的執行緒所呼叫，它們就會擲回 `improper_lock` 型別的例外狀況。  
  
> [!NOTE]
>  因為 `reader_writer_lock` 類別不可重新進入，所以您無法將唯讀鎖定升級至讀取器\/寫入器鎖定，或將讀取器\/寫入器鎖定降級至唯讀鎖定。  執行上述其中一項作業會產生不明的行為。  
  
### 方法和功能  
 下表列出 `reader_writer_lock` 類別所定義的重要方法。  
  
|方法|說明|  
|--------|--------|  
|[鎖定](../Topic/reader_writer_lock::lock%20Method.md)|取得鎖定的讀取\/寫入存取權。|  
|[try\_lock](../Topic/reader_writer_lock::try_lock%20Method.md)|嘗試取得鎖定的讀取\/寫入存取權，但是不封鎖。|  
|[lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md)|取得鎖定的唯讀存取權。|  
|[try\_lock\_read](../Topic/reader_writer_lock::try_lock_read%20Method.md)|嘗試取得鎖定的唯讀存取權，但是不封鎖。|  
|[unlock](../Topic/reader_writer_lock::unlock%20Method.md)|釋放鎖定。|  
  
 \[[上方](#top)\]  
  
##  <a name="scoped_lock"></a> scoped\_lock 和 scoped\_lock\_read  
 `critical_section` 和 `reader_writer_lock` 類別會提供巢狀 Helper 類別，可簡化您使用互斥物件的方式。  這些 Helper 類別稱為「*範圍鎖定*」\(Scoped Lock\)。  
  
 `critical_section` 類別包含 [concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) 類別。  此建構函式會取得所提供之 `critical_section` 物件的存取權，而解構函式則釋放該物件的存取權。  `reader_writer_lock` 類別包含與 `critical_section::scoped_lock` 很相似的 [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md) 類別，不過它會管理所提供之 `reader_writer_lock` 物件的寫入存取權。  `reader_writer_lock` 類別也包含 [concurrency::reader\_writer\_lock::scoped\_lock\_read](../Topic/reader_writer_lock::scoped_lock_read%20Class.md) 類別。  這個類別會管理所提供之 `reader_writer_lock` 物件的讀取存取權。  
  
 當您以手動方式使用 `critical_section` 和 `reader_writer_lock` 物件時，範圍鎖定可提供許多優點。  一般而言，您會將範圍鎖定配置於堆疊上。  範圍鎖定會在終結時自動釋放其互斥物件的存取權。因此，您不會以手動方式解除鎖定基礎物件。  當函式包含多個 `return` 陳述式時，這種鎖定會很有用。  範圍鎖定也可以協助您撰寫無例外狀況之虞的程式碼。  當 `throw` 陳述式導致堆疊回溯時，就會呼叫任何作用中範圍鎖定的解構函式，因此一定會正確釋放互斥物件。  
  
> [!NOTE]
>  當您使用 `critical_section::scoped_lock`、`reader_writer_lock::scoped_lock` 和 `reader_writer_lock::scoped_lock_read` 類別時，請勿手動釋放基礎互斥物件的存取權。  這樣做可能會讓執行階段處於無效的狀態。  
  
##  <a name="event"></a> event  
 [concurrency::event](../../parallel/concrt/reference/event-class.md) 類別代表其狀態可能是已收到信號或未收到信號的同步處理物件。  與用來保護共用資料之存取權的同步處理物件 \(例如關鍵區段\) 不同的是，事件會同步處理執行流程。  
  
 當某項工作已經完成另一項工作的內容時，`event` 類別就很有用。  例如，某項工作可能會通知另一項工作，表示它已經從網路連接或檔案中讀取資料。  
  
### 方法和功能  
 下表列出 `event` 類別所定義的許多重要方法。  
  
|方法|說明|  
|--------|--------|  
|[wait](../Topic/event::wait%20Method.md)|等候事件成為已收到信號。|  
|[set](../Topic/event::set%20Method.md)|將事件設定為已收到信號的狀態。|  
|[reset](../Topic/event::reset%20Method.md)|將事件設定為未收到信號的狀態。|  
|[wait\_for\_multiple](../Topic/event::wait_for_multiple%20Method.md)|等候多個事件成為已收到信號。|  
  
### 範例  
 如需示範如何使用 `event` 類別的範例，請參閱[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 \[[上方](#top)\]  
  
## 相關章節  
 [比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 比較同步處理資料結構的行為與 Windows API 所提供之同步處理資料結構的行為。  
  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)  
 描述「並行執行階段」，它可以簡化平行程式設計工作，而且包含相關主題的連結。