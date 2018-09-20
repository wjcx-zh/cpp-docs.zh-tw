---
title: 多執行緒： 何時使用 MFC 的同步處理類別 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 018623e9e6a093c4f86b8768e0fd5329f4ea3282
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443770"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>多執行緒： 何時使用 MFC 的同步處理類別

MFC 提供的多執行緒的類別分為兩類： 同步處理物件 ([CSyncObject](../mfc/reference/csyncobject-class.md)， [CSemaphore](../mfc/reference/csemaphore-class.md)， [CMutex](../mfc/reference/cmutex-class.md)， [CCriticalSection](../mfc/reference/ccriticalsection-class.md)，並[CEvent](../mfc/reference/cevent-class.md)) 和同步處理存取物件 ([CMultiLock](../mfc/reference/cmultilock-class.md)並[CSingleLock](../mfc/reference/csinglelock-class.md))。

必須控制資源的存取權，以確保資源的完整性時，會使用同步類別。 同步存取類別用來存取這些受控制的資源。 本主題說明何時使用每個類別。

若要判斷您應該使用哪一個同步處理類別，詢問一系列如下的問題：

1. 應用程式必須等到事情發生才可存取資源 （例如，資料必須從接收通訊連接埠之前寫入的檔案）？

     如果是，使用`CEvent`。

2. 可以多個執行緒中相同的應用程式存取此資源一次 （例如，您的應用程式允許最多五個具有相同的文件檢視的 windows）？

     如果是，使用`CSemaphore`。

3. 多個應用程式可以使用此資源 （例如，資源是在 DLL 中）？

     如果是，使用`CMutex`。

     若為否，使用`CCriticalSection`。

`CSyncObject` 是永遠不會直接使用。 它是其他四個同步處理類別的基底類別。

## <a name="example-1-using-three-synchronization-classes"></a>範例 1： 使用三個同步處理類別

例如，擷取應用程式維護帳戶的連結的清單。 此應用程式可讓最多三個帳戶，以在個別的視窗中加以檢查，但只有一個可以更新任何特定的時間。 更新帳戶時，更新的資料是透過網路傳送至資料封存。

此範例應用程式會使用三種同步處理的類別。 因為它可讓要檢查一次最多三個帳戶，它會使用`CSemaphore`限制三個檢視物件的存取權。 當嘗試檢視的第四個帳戶時，就會等候直到其中一個第三個視窗關閉或失敗的應用程式。 更新帳戶時，應用程式使用`CCriticalSection`來確保只有一個帳戶會更新一次。 更新成功之後，它會通知`CEvent`，這會釋放執行緒等待事件收到訊號。 此執行緒會將新的資料傳送至資料封存。

## <a name="example-2-using-synchronization-access-classes"></a>範例 2： 使用同步存取類別

選擇要使用哪一個同步存取類別則更加簡單。 如果存取單一受控制的資源，只有關您的應用程式，使用`CSingleLock`。 如果它需要存取多個受控制的任何的資源一個時，使用`CMultiLock`。 在範例 1，`CSingleLock`但已使用，因為每個案例中只有一個資源需要在任何特定時間。

如需如何使用同步類別的資訊，請參閱[多執行緒： 如何使用同步類別](multithreading-how-to-use-the-synchronization-classes.md)。 同步處理的相關資訊，請參閱[同步處理](/windows/desktop/Sync/synchronization)Windows SDK 中。 多執行緒 MFC 支援的詳細資訊，請參閱[c + + 和 MFC 的多執行緒](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)