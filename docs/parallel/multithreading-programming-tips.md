---
title: 多執行緒：MFC 程式設計提示
ms.date: 08/27/2018
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
ms.openlocfilehash: deaf53d7b337fd33214bbcc4567e73bd33345d49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511723"
---
# <a name="multithreading-mfc-programming-tips"></a>多執行緒：MFC 程式設計提示

多執行緒應用程式需要比單一執行緒應用程式更嚴格的處理, 以確保作業會依照預定的順序發生, 而由多個執行緒存取的任何資料也不會損毀。 本主題說明使用 Microsoft Foundation Class (MFC) 程式庫設計多執行緒應用程式時, 避免潛在問題的技術。

- [從多個執行緒存取物件](#_core_accessing_objects_from_multiple_threads)

- [從非 MFC 執行緒存取 MFC 物件](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Windows 控制碼對應](#_core_windows_handle_maps)

- [執行緒之間的通訊](#_core_communicating_between_threads)

##  <a name="_core_accessing_objects_from_multiple_threads"></a>從多個執行緒存取物件

MFC 物件本身不是安全線程。 除非您使用 MFC 同步處理類別和 (或) 適當的 Win32 同步處理物件 (例如重要區段), 否則兩個不同的執行緒無法操作相同的物件。 如需重要區段和其他相關物件的詳細資訊, 請參閱 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)處理。

類別庫會在內部使用重要區段來保護全域資料結構, 例如, 用於偵錯工具的記憶體配置。

##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>從非 MFC 執行緒存取 MFC 物件

如果您有多執行緒應用程式會以非使用[CWinThread](../mfc/reference/cwinthread-class.md)物件的方式建立執行緒, 則無法從該執行緒存取其他 MFC 物件。 換句話說, 如果您想要從次要執行緒存取任何 MFC 物件, 您必須使用多執行緒中[所述的其中一個方法來建立該執行緒:建立使用者介面執行緒](multithreading-creating-user-interface-threads.md)或[多執行緒:正在建立背景](multithreading-creating-worker-threads.md)工作執行緒。 這些方法是唯一的, 可讓類別庫初始化處理多執行緒應用程式所需的內部變數。

##  <a name="_core_windows_handle_maps"></a>Windows 控制碼對應

一般的規則是, 執行緒只能存取其所建立的 MFC 物件。 這是因為暫時性和永久性的 Windows 控制碼對應會保留線上程區域儲存區中, 以協助維護保護以防止同時從多個執行緒存取。 例如, 工作者執行緒無法執行計算, 然後呼叫檔的`UpdateAllViews`成員函式, 讓包含修改過新資料之 views 的視窗。 這完全不會有任何作用, 因為從`CWnd`物件到 hwnd 的對應是主要執行緒的本機。 這表示一個執行緒可能會有一個從 Windows 控制碼到C++物件的對應, 但另一個執行緒可能會將相同的控制碼C++對應至不同的物件。 在某個執行緒中所做的變更不會反映在另一個執行緒中。

有數種方式可解決此問題。 第一種方式是將個別控制碼 (例如 HWND) 傳遞給C++背景工作執行緒, 而不是物件。 背景工作執行緒會藉由呼叫適當`FromHandle`的成員函式, 將這些物件加入其暫存對應中。 您也可以藉由呼叫`Attach`, 將物件新增至執行緒的永久對應, 但只有在您保證物件的長度超過執行緒時, 才應該這麼做。

另一個方法是建立新的使用者自訂訊息, 其對應至您的工作者執行緒將執行的不同工作, 並使用`::PostMessage`將這些訊息發佈至應用程式的主視窗。 這種通訊方法與兩個不同的應用程式交談相似, 不同之處在于這兩個執行緒都是在相同的位址空間中執行。

如需控點對應的詳細資訊, 請參閱[技術提示 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 如需執行緒區域儲存區的詳細資訊, 請參閱[執行緒區域儲存區](/windows/win32/ProcThread/thread-local-storage)和在 Windows SDK 中[使用執行緒區域儲存](/windows/win32/ProcThread/using-thread-local-storage)區。

##  <a name="_core_communicating_between_threads"></a>執行緒之間的通訊

MFC 提供一些類別, 可讓執行緒同步處理物件的存取, 以維護執行緒的安全。 這些類別的使用方式會在[多執行緒中說明:如何使用同步處理類別](multithreading-how-to-use-the-synchronization-classes.md)和[多執行緒:使用同步處理類別](multithreading-when-to-use-the-synchronization-classes.md)的時機。 如需這些物件的詳細資訊, 請參閱 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)處理。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
