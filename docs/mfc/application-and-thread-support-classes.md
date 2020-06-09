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
ms.openlocfilehash: 7e64cc50a121f457b7e32e0ed549db2fa9950843
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619443"
---
# <a name="application-and-thread-support-classes"></a>應用程式和執行緒支援類別

每個應用程式只能有一個應用程式物件;這個物件會協調正在執行之程式中的其他物件，而且衍生自 `CWinApp` 。

Microsoft Foundation Class （MFC）程式庫支援在應用程式內執行多個執行緒。 所有應用程式都必須至少有一個執行緒;您的物件所使用的執行緒 `CWinApp` 是這個主要執行緒。

`CWinThread`封裝作業系統執行緒功能的一部分。 為了讓您更輕鬆地使用多個執行緒，MFC 也會提供同步處理物件類別，以提供 c + + 介面給 Win32 同步處理物件。

## <a name="application-and-thread-classes"></a>應用程式和執行緒類別

[CWinApp](reference/cwinapp-class.md)<br/>
封裝程式碼，以初始化、執行及終止應用程式。 您將從這個類別衍生您的應用程式物件。

[CWinThread](reference/cwinthread-class.md)<br/>
所有線程的基類。 `CWinThread`如果您的執行緒執行使用者介面函式，請直接使用，或從衍生類別。 `CWinApp` 衍生自 `CWinThread`。

## <a name="synchronization-object-classes"></a>同步處理物件類別

[CSyncObject](reference/csyncobject-class.md)<br/>
同步處理物件類別的基類。

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
同步處理類別，只允許單一進程內的一個執行緒存取物件。

[CSemaphore](reference/csemaphore-class.md)<br/>
同步處理類別，允許一到一或多個指定的同時存取物件數目。

[CMutex](reference/cmutex-class.md)<br/>
一種同步處理類別，只允許任何數目的進程內的一個執行緒存取物件。

[CEvent](reference/cevent-class.md)<br/>
同步處理類別，會在事件發生時通知應用程式。

[CSingleLock](reference/csinglelock-class.md)<br/>
用於安全線程類別的成員函式，以鎖定一個同步處理物件。

[CMultiLock](reference/cmultilock-class.md)<br/>
用在安全線程類別的成員函式中，從同步處理物件的陣列鎖定一或多個同步處理物件。

## <a name="related-classes"></a>相關類別

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
剖析用來啟動程式的命令列。

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
將等候游標放在螢幕上。 在冗長的作業期間使用。

[CDockState](reference/cdockstate-class.md)<br/>
處理控制列銜接狀態資料的持續性儲存。

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
維護最近使用的（MRU）檔案清單。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
