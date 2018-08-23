---
title: 多執行緒： 程式設計提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ad830117323aef807fcebc1ef61b4dfb1900bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591307"
---
# <a name="multithreading-programming-tips"></a>多執行緒：程式設計提示
存取資料時，多執行緒應用程式會需要更嚴格的注意，比單一執行緒應用程式。 因為有多個，獨立路徑中執行的同時使用多執行緒應用程式中，演算法、 資料或兩者都必須知道該資料可由多個執行緒一次。 本主題說明使用 Microsoft Foundation Class (MFC) 程式庫的多執行緒應用程式進行程式設計時，避免發生潛在問題的技術。  
  
- [從多個執行緒存取的物件](#_core_accessing_objects_from_multiple_threads)  
  
- [從非 MFC 執行緒存取 MFC 物件](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
- [Windows 控制代碼對應](#_core_windows_handle_maps)  
  
- [執行緒之間進行通訊](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> 從多個執行緒存取的物件  
 
大小和效能因素，MFC 物件不是安全執行緒在物件層級，只能在類別層級。 這表示您可以管理兩個不同的兩個個別的執行緒`CString`物件，但不是操作相同的兩個執行緒`CString`物件。 如果您一定要有多個執行緒操作相同的物件，請使用適當的 Win32 同步處理機制，例如關鍵區段來保護這類存取權。 如需關鍵區段和其他相關物件，請參閱 <<c0> [ 同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)Windows SDK 中。  
  
類別庫內部使用重要區段保護全域資料結構，例如所使用的偵錯記憶體配置。  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 從非 MFC 執行緒存取 MFC 物件  
 
如果您有多執行緒的應用程式，以建立執行緒以外使用方式[CWinThread](../mfc/reference/cwinthread-class.md)物件時，您無法從該執行緒來存取其他 MFC 物件。 換句話說，如果您想要從次要執行緒存取任何 MFC 物件時，您必須建立該執行緒中所述的方法之一[多執行緒： 建立使用者介面執行緒](../parallel/multithreading-creating-user-interface-threads.md)或[多執行緒：建立背景工作執行緒](../parallel/multithreading-creating-worker-threads.md)。 這些方法是唯一可讓類別庫，來初始化內部處理多執行緒應用程式所需的變數。  
  
##  <a name="_core_windows_handle_maps"></a> Windows 控制代碼對應  
 
一般而言，執行緒可以存取它所建立的 MFC 物件。 這是因為暫時性和永久性的 Windows 控制代碼對應保存在協助維護從多個執行緒同時存取的執行緒區域儲存區。 例如，背景工作執行緒無法執行計算，並接著呼叫文件的`UpdateAllViews`成員函式來包含新的資料修改檢視上的 windows。 這有任何作用，因為從地圖`CWnd`Hwnd 的物件是在本機的主要執行緒。 這表示一個執行緒可能已從 Windows 控制代碼的對應至 c + + 物件，但另一個執行緒可能會將該相同的控制代碼對應到不同的 c + + 物件。 一個執行緒中所做的變更不會反映在其他。  
  
有幾種方式解決這個問題。 第一個是將個別的處理常式 （例如 HWND) 而不是在背景工作執行緒的 c + + 物件。 背景工作執行緒然後將這些物件加入其暫存對應藉由呼叫適當`FromHandle`成員函式。 您也可以加入至執行緒的永久對應物件，藉由呼叫`Attach`，但這應該只有在您保證物件會存在時間超過執行緒完成。  
  
若要建立新使用者定義訊息對應至不同的工作會執行您的背景工作執行緒，並將這些訊息張貼至應用程式的主視窗的另一個方法是使用`::PostMessage`。 此通訊方式類似於轉換，除了這兩個執行緒正在執行相同的位址空間中的兩個不同應用程式。  
  
如需有關處理常式對應的詳細資訊，請參閱[技術的附註 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 如需執行緒區域儲存區的詳細資訊，請參閱[執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686749)並[使用執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686991)Windows SDK 中。  
  
##  <a name="_core_communicating_between_threads"></a> 執行緒之間進行通訊  
 
MFC 提供類別，可讓同步處理以維護執行緒安全性物件的存取權的執行緒數目。 這些類別的用法所述[多執行緒： 如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)並[多執行緒： 何時使用同步類別](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。 如需有關這些物件的詳細資訊，請參閱 <<c0> [ 同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  

[使用 C++ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)