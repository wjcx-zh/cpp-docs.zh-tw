---
title: "&lt;future&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<future>"
dev_langs: 
  - "C++"
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;future&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含標準標頭\<未來\>定義樣板類別並支援能夠簡化執行程式的樣板—很可能是分開的執行緒—和接收結果。  結果是由函式傳回的值或是函式發出的例外狀況，但此狀況並非在函式中發現。  
  
 此標題使用並行執行階段 \(ConcRT\)，以便與其他 ConcRT 機制一起使用。  如需 ConcRT 的詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。  
  
## 語法  
  
```cpp  
#include <future>  
```  
  
## 備註  
  
> [!NOTE]
>  以 **\/clr** 或 **\/clr:pure** 編譯的程式碼，這個標題會封鎖。  
  
 *非同步提供者* 儲存函式呼叫的結果。  *非同步傳回物件* 用來擷取函式呼叫的結果。   *有相關聯的非同步狀態* 提供非同步提供者和一或多個非同步傳回物件之間的通訊。  
  
 程式不會直接建立任何相關聯的非同步狀態物件。  程式會建立非同步提供者，當它需要建立一個非同步傳回物件，且此物件享有其提供者的關聯性同步狀態。  非同步提供者和非同步傳回物件處理保留它們共用關聯的非同步狀態物件。  當參考這個關聯非同步狀態的最後一個物件釋放時，這個物件相關聯的非同步狀態終結。  
  
 非同步提供者或沒有相關聯的非同步傳回物件狀態是 *空的 \(empty\)*。  
  
 只有在非同步提供者儲存傳回值或儲存例外狀況後，關聯的非同步狀態才會成為*就緒*。  
  
 樣板函式 `async` 和樣板類別 `promise` 和 `packaged_task` 都是非同步提供者。  樣板類別 `future` 和 `shared_future` 描述非同步傳回物件。  
  
 每個範本 `promise`， `future`，和 `shared_future` 具有型別 `void` 也有部分儲存特製化和接收參考的值。  這些特製化與主要只範本有儲存和擷取傳回值的函式簽章和語意。  
  
 樣板類別 `future` 和 `shared_future` 在其解構函式永遠不會封鎖，除了提供回溯相容性 \(Backward Compatibility\) 儲存的一種情況:不同於其他未來，，以 `future`—或— `shared_future`最後一個附加至工作啟動以 `std::async`，解構函式區塊，如果工作未完成;即會封鎖，則執行緒未呼叫 `.get()` 或 `.wait()` 和工作仍在執行中。  下列可用性附註已加入至 `std::async`的標準草稿中 :「\[注意:如果未來從 std::async 移至地區範圍時，使用未來的其他程式碼須注意未來可能對共享狀態造成封鎖的解構函式可能潛藏其中。—結束註解\]」在其他情況下， `future` 和 `shared_future` 解構函式要求並保證封鎖永遠不會發生。  
  
## 成員  
  
### 類別  
  
|Name|說明|  
|----------|--------|  
|[future 類別](../standard-library/future-class.md)|描述一個非同步傳回物件。|  
|[future\_error 類別](../standard-library/future-error-class.md)|描述一個可以用型別方法傳回處理 `future` 物件的例外狀況物件。|  
|[packaged\_task 類別](../standard-library/packaged-task-class.md)|描述一個為呼叫包裝含式的非同步提供者，其呼叫簽章是 `Ty(ArgTypes...)`。  除了潛在的結果之外，其與非同步狀態的相關聯擁有物件的可呼叫複本。|  
|[promise 類別](../standard-library/promise-class.md)|描述一個非同步提供者。|  
|[shared\_future 類別](../standard-library/shared-future-class.md)|描述一個非同步傳回物件。  與 `future` 物件相比，非同步提供者可以與任何數目的 `shared_future` 物件相關聯。|  
  
### 結構  
  
|Name|說明|  
|----------|--------|  
|[is\_error\_code\_enum 結構](../standard-library/is-error-code-enum-structure.md)|表示 `future_errc` 的特製化適用於儲存 `error_code`。|  
|[uses\_allocator 結構](../standard-library/uses-allocator-structure.md)|一律套用於特製化。|  
  
### 函式  
  
|Name|說明|  
|----------|--------|  
|[async 函式](../Topic/async%20Function.md)|表示非同步提供者。|  
|[future\_category 函式](../Topic/future_category%20Function.md)|傳回對 Draw 錯誤與 `future` 物件相關聯之 `error_category` 物件的參考。|  
|[make\_error\_code 函式](../Topic/make_error_code%20Function.md)|建立具有 `error_code` 的`error_category`物件，且此物件繪製 `future` 錯誤 。|  
|[make\_error\_condition 函式](../Topic/make_error_condition%20Function.md)|建立具有 `error_condition` 的`error_category`物件，且此物件繪製 `future` 錯誤 。|  
|[swap 函式 \(\<future\>\)](../Topic/swap%20Function%20\(%3Cfuture%3E\).md)|與另一個物件交換一個 `promise` 相關聯的非同步狀態。|  
  
### 列舉  
  
|Name|說明|  
|----------|--------|  
|[future\_errc 列舉](../Topic/future_errc%20Enumeration.md)|由 `future_error` 類別所報告的錯誤提供符號名稱。|  
|[future\_status 列舉](../Topic/future_status%20Enumeration.md)|一個需要時間等候的函式回傳提供符號名稱。|  
|[launch 列舉](../Topic/launch%20Enumeration.md)|表示描述樣板函式的 `async`可能方法位元遮罩型別。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)