---
title: 應用程式和執行緒支援類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 5f69ea6a87d0e1ae16a6079a414d623af6dd88fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496251"
---
# <a name="application-and-thread-support-classes"></a>應用程式和執行緒支援類別

每個應用程式都有一個應用程式物件;此物件會協調執行中的程式中的其他物件，並衍生自`CWinApp`。

Microsoft Foundation Class (MFC) 程式庫支援多執行緒的應用程式內執行。 必須至少一個執行緒; 所有的應用程式。所使用的執行緒您`CWinApp`物件是這個主要執行緒。

`CWinThread` 封裝的作業系統執行緒功能的一部分。 若要讓多個執行緒更方便使用，MFC 也提供同步處理提供 c + + 物件的介面，Win32 同步處理的物件類別。

## <a name="application-and-thread-classes"></a>應用程式和執行緒類別

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
封裝程式碼以初始化、 執行和終止應用程式。 您將會從這個類別衍生您的應用程式物件。

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
所有的執行緒基底類別。 直接使用，或自`CWinThread`如果您的執行緒會執行使用者介面功能。 `CWinApp` 衍生自 `CWinThread`。

## <a name="synchronization-object-classes"></a>同步處理的物件類別

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
同步處理物件類別的基底類別。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
只允許一個執行緒來存取物件的單一處理序內的同步處理類別。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
同步處理類別可介於 1 到指定的最大同時存取的物件數目。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
只允許一個執行緒內任意數目的處理程序來存取物件的同步處理類別。

[CEvent](../mfc/reference/cevent-class.md)<br/>
同步處理類別，在事件發生時通知應用程式。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
用於安全執行緒類別的成員函式，以鎖定一個同步處理物件。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
用於安全執行緒類別的成員函式，以鎖定的一或多個同步處理物件，從同步處理物件的陣列。

## <a name="related-classes"></a>相關的類別

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
剖析命令列與您的程式已啟動。

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
將等待游標放在螢幕上。 在 長時間作業期間使用。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
處理停駐控制列的狀態資料的永續性儲存的體。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
會維護最近使用過的 (MRU) 檔案清單。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

