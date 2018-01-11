---
title: "多執行緒： 何時使用同步類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38437983552dfdf2cf6708ec5fd067e06387ea5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>多執行緒：何時使用同步類別
MFC 提供的多執行緒的類別分為兩類： 同步處理物件 ([CSyncObject](../mfc/reference/csyncobject-class.md)， [CSemaphore](../mfc/reference/csemaphore-class.md)， [CMutex](../mfc/reference/cmutex-class.md)， [CCriticalSection](../mfc/reference/ccriticalsection-class.md)，和[CEvent](../mfc/reference/cevent-class.md)) 和同步處理存取物件 ([CMultiLock](../mfc/reference/cmultilock-class.md)和[CSingleLock](../mfc/reference/csinglelock-class.md))。  
  
 必須控制資源的存取權，以確保資源的完整性時，會使用同步類別。 同步存取類別可用來存取這些受控制的資源。 本主題說明何時使用每個類別。  
  
 若要判斷您應該使用哪一個同步處理類別，請詢問下列一系列的問題：  
  
1.  應用程式必須等到發生才可存取資源 （例如，資料必須從接收通訊連接埠之前寫入的檔案）？  
  
     如果是，請使用`CEvent`。  
  
2.  可以多個執行緒中相同的應用程式存取此資源一次 （例如，您的應用程式允許最多五個使用相同的文件的檢視表的 windows）？  
  
     如果是，請使用`CSemaphore`。  
  
3.  多個應用程式可以使用此資源 （例如，資源是在 DLL 中）？  
  
     如果是，請使用`CMutex`。  
  
     若為否，使用`CCriticalSection`。  
  
 **CSyncObject**永遠不會直接使用。 它是其他四個同步處理類別的基底類別。  
  
## <a name="example-1-using-three-synchronization-classes"></a>範例 1： 使用三個同步處理類別  
 例如，讓應用程式維護帳戶的連結的清單。 此應用程式可讓多達三個帳戶，以檢查在個別視窗中，但只有一個可以更新任何特定時間。 更新帳戶時，更新的資料會透過網路傳送到資料封存。  
  
 此範例應用程式會使用所有的三種類型的同步處理的類別。 因為它可讓多達三個帳戶，以檢查一次，它會使用`CSemaphore`限制存取三個檢視表物件。 當嘗試檢視的第四個帳戶發生時，應用程式會等候直到前三個視窗關閉，否則便會失敗。 應用程式的帳戶更新時，使用`CCriticalSection`以確保只有一個帳戶會更新一次。 更新成功之後，它會通知`CEvent`，其中釋放執行緒等待事件發出信號。 此執行緒會將新的資料傳送至資料封存。  
  
## <a name="example-2-using-synchronization-access-classes"></a>範例 2： 使用同步存取類別  
 選擇要使用哪一個同步存取類別會更加簡單。 如果存取單一受控制的資源，只有關您的應用程式，使用`CSingleLock`。 如果它必須存取其中一個受控制的資源數目，請使用`CMultiLock`。 在範例 1，`CSingleLock`可能已用，因為每個案例中只有一個資源需要在任何特定時間。  
  
 如需如何使用同步類別的資訊，請參閱[多執行緒： 如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)。 同步處理的相關資訊，請參閱[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 多執行緒 MFC 支援的詳細資訊，請參閱[多執行緒 c + + 和 MFC](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)