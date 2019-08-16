---
title: 比較同步處理資料結構與 Windows API
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510587"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>比較同步處理資料結構與 Windows API

本主題會比較並行執行階段所提供的同步處理資料結構與 Windows API 所提供的行為。

並行執行階段所提供的同步處理資料結構會遵循合作式*執行緒模型*。 在合作式執行緒模型中, 同步處理原始物件會明確地將其處理資源產生到其他執行緒。 這不同于*搶先式執行緒模型*, 其中處理資源會由控制排程器或作業系統傳輸到其他執行緒。

## <a name="critical_section"></a>critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)類別類似于 Windows `CRITICAL_SECTION`結構, 因為它只能由一個進程的執行緒使用。 如需 Windows API 中重要區段的詳細資訊, 請參閱[重要區段物件](/windows/win32/Sync/critical-section-objects)。

## <a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)類別類似于 Windows 超薄讀取器/寫入器 (SRW) 鎖定。 下表說明兩者的相似性和差異。

|功能|`reader_writer_lock`|SRW 鎖定|
|-------------|--------------------------|--------------|
|不可重新進入|是|是|
|可以將讀取器升級為寫入器 (升級支援)|否|否|
|可以將寫入器降級為讀取器 (降級支援)|否|否|
|寫入喜好設定鎖定|是|否|
|對寫入器的 FIFO 存取|是|否|

如需 SRW 鎖定的詳細資訊, 請參閱 Platform SDK 中的[超薄讀取器/寫入器 (SRW) 鎖定](/windows/win32/sync/slim-reader-writer--srw--locks)。

## <a name="event"></a>event

[Concurrency:: 事件](../../parallel/concrt/reference/event-class.md)類別類似于未命名的 Windows 手動重設事件。 不過, `event`物件會以合作方式運作, 而 Windows 事件的行為事先。 如需 Windows 事件的詳細資訊, 請參閱[事件物件](/windows/win32/Sync/event-objects)。

## <a name="example"></a>範例

### <a name="description"></a>說明

若要進一步瞭解`event`類別和 Windows 事件之間的差異, 請考慮下列範例。 這個範例可讓排程器建立最多兩個同時執行的工作, 然後呼叫使用`event`類別和 Windows 手動重設事件的兩個類似函式。 每個函式會先建立數個等待共用事件變成信號的工作。 然後, 每個函式都會產生執行中的工作, 然後對事件發出信號。 然後, 每個函式都會等候訊號事件。

### <a name="code"></a>程式碼

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>註解

這個範例會產生下列範例輸出:

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

`event`因為類別會以合作方式運作, 所以排程器可以在事件等候進入已發出信號的狀態時, 將處理資源重新配置給另一個內容。 因此, 使用`event`類別的版本會完成更多工具。 在使用 Windows 事件的版本中, 每個等待工作都必須進入 [已通知] 狀態, 然後才會啟動下一個工作。

如需工作的詳細資訊, 請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

## <a name="see-also"></a>另請參閱

[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)
