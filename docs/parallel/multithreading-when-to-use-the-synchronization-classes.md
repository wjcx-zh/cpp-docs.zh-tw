---
title: 多執行緒：使用 MFC 同步處理類別的時機
ms.date: 08/27/2018
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511994"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>多執行緒：使用 MFC 同步處理類別的時機

MFC 提供的多執行緒類別分為兩類: 同步處理物件 ([CSyncObject](../mfc/reference/csyncobject-class.md)、 [CSemaphore](../mfc/reference/csemaphore-class.md)、 [CMutex](../mfc/reference/cmutex-class.md)、 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)和[CEvent](../mfc/reference/cevent-class.md)) 和同步處理存取物件 ([CMultiLock](../mfc/reference/cmultilock-class.md)和[CSingleLock](../mfc/reference/csinglelock-class.md))。

當必須控制對資源的存取, 以確保資源的完整性時, 會使用同步處理類別。 同步存取類別是用來取得這些受控制資源的存取權。 本主題描述每個類別的使用時機。

若要判斷應該使用哪一個同步處理類別, 請詢問下列一系列的問題:

1. 應用程式是否必須等到發生問題才能存取資源 (例如, 必須先從通訊埠接收資料, 才能將其寫入檔案)？

   如果是, 請`CEvent`使用。

2. 同一個應用程式中的多個執行緒可以一次存取此資源 (例如, 您的應用程式最多允許在相同檔上有五個具有視圖的視窗)？

   如果是, 請`CSemaphore`使用。

3. 有多個應用程式可以使用此資源 (例如, 資源是在 DLL 中) 嗎？

   如果是, 請`CMutex`使用。

   如果不是, `CCriticalSection`請使用。

`CSyncObject`永遠不會直接使用。 這是其他四個同步處理類別的基類。

## <a name="example-1-using-three-synchronization-classes"></a>範例 1：使用三個同步處理類別

例如, 建立一個應用程式來維護帳戶的連結清單。 此應用程式允許在個別的視窗中檢查最多三個帳戶, 但在任何特定時間只能更新一個帳戶。 當帳戶更新時, 更新的資料會透過網路傳送到資料封存。

這個範例應用程式會使用所有三種類型的同步處理類別。 因為它允許一次檢查最多三個帳戶, 所以它會使用`CSemaphore`來限制對三個 view 物件的存取。 當嘗試查看第四個帳戶時, 應用程式會等待前三個視窗中的其中一個關閉或失敗。 當帳戶更新時, 應用程式會使用`CCriticalSection`來確保一次只會更新一個帳戶。 更新成功之後, 它會發出`CEvent`信號, 這會釋放等待事件信號的執行緒。 此執行緒會將新的資料傳送至資料封存。

## <a name="example-2-using-synchronization-access-classes"></a>範例 2：使用同步存取類別

選擇要使用的同步存取類別, 甚至更簡單。 如果您的應用程式只關心存取單一受控制的資源, `CSingleLock`請使用。 如果需要存取數個受控制資源的任何一個, 請使用`CMultiLock`。 在範例 1 `CSingleLock`中, 會使用, 因為在每個案例中, 任何特定時間只需要一個資源。

如需如何使用同步處理類別的詳細資訊, [請參閱多執行緒:如何使用同步處理類別](multithreading-how-to-use-the-synchronization-classes.md)。 如需同步處理的相關資訊, 請參閱 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)處理。 如需 MFC 中多執行緒支援的詳細資訊, 請參閱[使用和 MFC 進行C++多執行緒處理](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
