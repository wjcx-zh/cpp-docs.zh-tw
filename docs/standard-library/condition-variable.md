---
title: "&lt;condition_variable&gt; | Microsoft Docs"
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
  - "<condition_variable>"
dev_langs: 
  - "C++"
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;condition_variable&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義用於建立物件等候條件變成 True 的 [condition\_variable](../standard-library/condition-variable-class.md) 和 [condition\_variable\_any](../standard-library/condition-variable-any-class.md) 類別。  
  
 此標題使用並行執行階段 \(ConcRT\)，以便與其他 ConcRT 機制一起使用。  如需 ConcRT 的詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。  
  
## 語法  
  
```cpp  
#include <condition_variable>  
```  
  
> [!NOTE]
>  以 **\/clr** 或 **\/clr:pure** 編譯的程式碼，這個標題會封鎖。  
  
### 備註  
 程式碼等候條件變數也必須使用 `mutex`。  對呼叫的執行緒必須鎖定 `mutex` ，在呼叫等候條件變數的函式。  當呼叫的函式傳回時， `mutex` 會鎖定。  當執行緒等候條件變成 True 時， `mutex` 未鎖定。  因此不會產生無法預期的結果，等候條件變數中的每個執行緒都必須使用相同的 `mutex` 物件。  
  
 `condition_variable_any` 型別的物件可以與任何型別 Mutex。  使用 Mutex 的型別不需要提供 `try_lock` 方法。  `condition_variable` 型別的物件只能與型別 `unique_lock<mutex>`Mutex。  這個型別的物件比型別 `condition_variable_any<unique_lock<mutex>>`物件可以快速。  
  
 若要等候事件，請先鎖定 Mutex，然後呼叫其中一個條件變數的 `wait` 方法。  在另一個的 `wait` 呼叫會封鎖執行緒信號狀態變數。  
  
 *false 喚醒* 發生，當等候條件變數的執行緒變成解除封鎖，而不用適當的告知。  若要辨識這類 false 喚醒，等候條件變成 True 的程式碼應該明確地檢查條件，當從等候程式碼傳回函式時。  使用迴圈，這通常是;您可以使用 `wait(unique_lock<mutex>& lock, Predicate pred)` 執行此迴圈。  
  
```cpp  
while (condition is false)  
    wait for condition variable;  
```  
  
 `condition_variable_any` 和 `condition_variable` 將每個分類都有等待條件的三種方法。  
  
-   `wait` 會無限制的時間。  
  
-   在指定之 `time`的`wait_until` 等候。  
  
-   `wait_for` 會指定 `time interval`。  
  
 每個方法有兩個多載版本。  等候並可能偽造地喚醒。  其他採用定義述詞的額外的樣板引數。  方法不會傳回，直到述詞是 `true`。  
  
 每個類別也會用來通知情況變數的兩個方法其條件為 `true`。  
  
-   `notify_one` 會喚醒等候條件變數的其中一個執行緒。  
  
-   `notify_all` 會喚醒等候條件變數的所有執行緒。  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [condition\_variable 類別](../standard-library/condition-variable-class.md)   
 [condition\_variable\_any 類別](../standard-library/condition-variable-any-class.md)   
 [cv\_status 列舉](../Topic/cv_status%20Enumeration.md)