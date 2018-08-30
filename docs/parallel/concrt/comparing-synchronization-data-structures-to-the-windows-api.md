---
title: 比較 Windows API 的同步處理資料結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb6dc90a272c8e288a4370ae18ad3d1fda150eed
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197544"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>比較同步處理資料結構與 Windows API
本主題會比較同步處理資料結構所提供的 Windows API 所提供之並行執行階段的行為。  
  
 並行執行階段所提供的同步處理資料結構遵循*合作式執行緒模型*。 在合作式執行緒模型中，同步處理原始物件來明確地產生它們的處理資源的其他執行緒。 這不同於*先佔式執行緒模型*，其中處理資源會轉移到其他執行緒所控制的排程器或作業系統。  
  
## <a name="criticalsection"></a>critical_section  
 [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)類別類似於 Windows`CRITICAL_SECTION`結構，因為它可供只能有一個處理序執行緒。 如需 Windows API 中的重要區段的詳細資訊，請參閱[重要區段物件](/windows/desktop/Sync/critical-section-objects)。  
  
## <a name="readerwriterlock"></a>reader_writer_lock  
 [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)類別類似於 Windows 輕型讀取器/寫入器 (SRW) 鎖定。 下表說明的相似性與差異。  
  
|功能|`reader_writer_lock`|SRW 鎖定|  
|-------------|--------------------------|--------------|  
|非可重新進入|是|是|  
|可以升級至寫入器 （升級支援） 的讀取器|否|否|  
|可以降級的讀取器 （不支援降級） 的寫入器|否|否|  
|寫入喜好設定鎖定|是|否|  
|寫入器的 FIFO 存取|是|否|  
  
 如需 SRW 鎖定的詳細資訊，請參閱[輕型讀取器/寫入器 (SRW) 鎖定](https://msdn.microsoft.com/library/windows/desktop/aa904937)平台 SDK 中。  
  
## <a name="event"></a>事件  
 [Concurrency:: event](../../parallel/concrt/reference/event-class.md)類別類似於未命名的 Windows 手動重設事件。 不過，`event`物件行為以合作方式，而 Windows 事件事先行為。 如需有關 Windows 事件的詳細資訊，請參閱 <<c0> [ 事件物件](/windows/desktop/Sync/event-objects)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 若要深入了解之間的差異`event`類別和 Windows 事件，請考慮下列的範例。 這個範例會啟用排程器，建立最多兩項同時工作，然後呼叫類似的兩個函式使用`event`類別和 Windows 的手動重設事件。 每個函式會先建立等候共用的事件變成收到訊號的幾項工作。 每個函式接著會產生要執行的工作，然後發出訊號的事件。 每個函式然後等候信號的事件。  
  
### <a name="code"></a>程式碼  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### <a name="comments"></a>註解  
 此範例會產生下列的範例輸出：  
  
```Output  
Cooperative event:  
    Context 0: waiting on an event.  
    Context 1: waiting on an event.  
    Context 2: waiting on an event.  
    Context 3: waiting on an event.  
    Context 4: waiting on an event.  
    Setting the event.  
    Context 5: received the event.  
    Context 6: received the event.  
    Context 7: received the event.  
    Context 8: received the event.  
    Context 9: received the event.  
Windows event:  
    Context 10: waiting on an event.  
    Context 11: waiting on an event.  
    Setting the event.  
    Context 12: received the event.  
    Context 14: waiting on an event.  
    Context 15: received the event.  
    Context 16: waiting on an event.  
    Context 17: received the event.  
    Context 18: waiting on an event.  
    Context 19: received the event.  
    Context 13: received the event.  
```  
  
 因為`event`類別的行為以合作方式，排程器可以重新配置到另一個內容的處理資源，當事件在等候輸入收到信號的狀態。 因此，所使用的版本來完成更多工作`event`類別。 在使用 Windows 事件的版本，之後才啟動下一個工作每個等待中工作時，必須輸入收到信號的狀態。  
  
 如需有關工作的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="see-also"></a>另請參閱  
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)
