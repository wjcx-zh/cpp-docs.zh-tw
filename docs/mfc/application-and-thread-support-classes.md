---
title: "應用程式和執行緒支援類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.support
dev_langs: C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e443c2393d9d3a8a0f61df6adddb2c83e7672723
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="application-and-thread-support-classes"></a>應用程式和執行緒支援類別
每個應用程式有只有一個應用程式物件。此物件會協調執行的程式中的其他物件，並衍生自`CWinApp`。  
  
 Microsoft Foundation Class (MFC) 程式庫支援應用程式內執行多個的執行緒。 所有應用程式必須有至少一個執行緒。所使用的執行緒程式`CWinApp`物件是這個主要執行緒。  
  
 `CWinThread`封裝作業系統執行緒功能的一部分。 若要讓使用多執行緒更容易，MFC 也提供同步處理提供 c + + 物件的介面，Win32 同步處理的物件類別。  
  
## <a name="application-and-thread-classes"></a>應用程式和執行緒類別  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 封裝程式碼以初始化、 執行和終止應用程式。 您將會從這個類別衍生應用程式物件。  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 所有執行緒基底類別。 直接使用，或自`CWinThread`如果您的執行緒會執行使用者介面功能。 `CWinApp` 衍生自 `CWinThread`。  
  
## <a name="synchronization-object-classes"></a>同步處理物件類別  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 同步處理物件類別的基底類別。  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 只允許一個執行緒存取物件的單一處理序中的同步處理類別。  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 同步處理類別可介於 1 到指定的最大同時存取的物件數目。  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 同步處理類別，只允許一個執行緒內任何數目的處理程序來存取的物件。  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 同步處理類別有事件發生時，通知應用程式。  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 用於安全執行緒類別的成員函式，以一個同步處理物件上的鎖定。  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 使用安全執行緒類別的成員函式來鎖定的一或多個同步處理物件，從同步處理物件的陣列。  
  
## <a name="related-classes"></a>相關的類別  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 剖析命令列與您的程式已啟動。  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 將等待游標放在螢幕上。 長時間作業期間使用。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 處理永續性儲存體的停駐控制列的狀態資料。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 會維護最近使用過的 (MRU) 檔案清單。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

