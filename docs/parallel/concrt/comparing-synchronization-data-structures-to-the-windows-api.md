---
title: "比較同步處理資料結構與 Windows API | Microsoft Docs"
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
  - "同步處理資料結構，與 Windows API 比較"
  - "事件類別，範例"
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 比較同步處理資料結構與 Windows API
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題會比較並行執行階段所提供的同步處理資料結構與 Windows API 所提供的同步處理資料結構在行為上的差異。  
  
 並行執行階段所提供的同步處理資料結構是遵循「*合作式執行緒模型*」\(Cooperative Threading Model\)。  在合作式執行緒模型中，同步處理原始型別會將自己的處理資源讓給其他執行緒。  這不同於「*先佔式執行緒模型*」\(Preemptive Threading Model\)，在該模型中，處理資源是由控制端排程器或作業系統轉給其他執行緒。  
  
## critical\_section  
 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 類別與 Windows `CRITICAL_SECTION` 結構類似，因為只有同處理序的執行緒才能使用它。  如需 Windows API 中之關鍵區段的詳細資訊，請參閱[關鍵區段物件](http://msdn.microsoft.com/library/windows/desktop/ms682530)。  
  
## reader\_writer\_lock  
 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 類別與 Windows 輕型讀取器\/寫入器 \(SRW\) 鎖定類似。  下表說明相似和相異處。  
  
|功能|`reader_writer_lock`|SRW 鎖定|  
|--------|--------------------------|------------|  
|不可重新進入|有|有|  
|可以將讀取器升階為寫入器 \(升級支援\)|沒有|沒有|  
|可以將寫入器降階為讀取器 \(降級支援\)|沒有|沒有|  
|寫入偏好設定鎖定|有|沒有|  
|對寫入器的 FIFO 存取|有|沒有|  
  
 如需 SRW 鎖定的詳細資訊，請參閱 Platform SDK 中的[輕型讀取器\/寫入器 \(SRW\) 鎖定](http://msdn.microsoft.com/library/windows/desktop/aa904937)。  
  
## event  
 [concurrency::event](../../parallel/concrt/reference/event-class.md) 類別與未命名的 Windows 手動重設事件類似。  不過，`event` 物件是以合作方式運作，而 Windows 事件則是以先佔方式運作。  如需 Windows 事件的詳細資訊，請參閱[事件物件](http://msdn.microsoft.com/library/windows/desktop/ms682655)。  
  
## 範例  
  
### 說明  
 若要更加了解 `event` 類別和 Windows 事件的差異，請參考下列範例。  這個範例會允許排程器最多建立兩個同時執行的工作，接著它會呼叫兩個類似的函式 \(這兩個函式使用 `event` 類別和 Windows 手動重設事件\)。  每個函式都會先建立數個工作，這些工作會等候某個共用事件變成已發出信號狀態。  每個函式接著會將資源讓給執行中的工作，然後發出事件的信號。  每個函式然後會等候所發出信號的事件。  
  
### 程式碼  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/CPP/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### 註解  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出：  
  
  **與對等:**  
 **內容 0:等候事件。**  
 **內容 1:等候事件。**  
 **內容 2:等候事件。**  
 **內容 3:等候事件。**  
 **內容 4:等候事件。**  
 **設定事件。**  
 **內容 5:接收事件。**  
 **內容 6:接收事件。**  
 **內容 7:接收事件。**  
 **內容 8:接收事件。**  
 **內容 9:接收事件。**  
**Windows 事件:**  
 **內容 10:等候事件。**  
 **內容 11:等候事件。**  
 **設定事件。**  
 **內容 12:接收事件。**  
 **內容 14:等候事件。**  
 **內容 15:接收事件。**  
 **內容 16:等候事件。**  
 **內容 17:接收事件。**  
 **內容 18:等候事件。**  
 **內容 19:接收事件。**  
 **內容 13:接收事件。** 因為 `event` 類別是以合作方式運作，所以排程器可以在有事件等候進入已發出信號狀態時，將處理資源重新配置給另一個內容。  因此，使用 `event` 類別的版本可以完成更多的工作。  在使用 Windows 事件的版本中，每個等候中的工作都必須先進入已發出信號狀態，下一個工作才會啟動。  
  
 如需工作的詳細資訊，請參閱 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 請參閱  
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)   
 [關鍵區段物件](http://msdn.microsoft.com/library/windows/desktop/ms682530)   
 [輕型讀取器\/寫入器鎖定 \(SRW\)](http://msdn.microsoft.com/library/windows/desktop/aa904937)   
 [事件物件](http://msdn.microsoft.com/library/windows/desktop/ms682655)