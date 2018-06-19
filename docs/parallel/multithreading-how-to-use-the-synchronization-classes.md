---
title: 多執行緒： 如何使用同步類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49b0737a794216c4899b280bc049a1cdc0fe0948
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689021"
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>多執行緒：如何使用同步類別
撰寫多執行緒應用程式時，同步處理執行緒之間的資源存取權是常見的問題。 有兩個或多個執行緒同時存取相同的資料可能會導致不必要和無法預期的結果。 例如，一個執行緒可能在更新結構的內容而另一個執行緒正在讀取相同結構的內容。 它是未知資料讀取的執行緒會收到： 舊的資料、 新撰寫的資料，或可能是兩者的混合。 MFC 提供一些同步處理和同步處理存取類別，來協助解決這個問題。 本主題說明可用的類別，以及如何使用它們來建立一般的多執行緒應用程式中的安全執行緒類別。  
  
 一般的多執行緒應用程式有類別，代表在執行緒之間共用的資源。 適當地設計、 完整的安全執行緒類別不需要呼叫任何同步處理函式。 所有項目是在內部處理此類別，可讓您專注於如何充分利用類別，沒有關於如何它可能會損毀的原因。 建立完整的安全執行緒類別的有效技術是同步處理類別合併資源類別。 同步類別合併到共用的類別是簡單的程序。  
  
 例如，讓應用程式維護帳戶的連結的清單。 此應用程式可讓多達三個帳戶，以檢查在個別視窗中，但只有一個可以更新任何特定時間。 更新帳戶時，更新的資料會透過網路傳送到資料封存。  
  
 此範例應用程式會使用所有的三種類型的同步處理的類別。 因為它可讓多達三個帳戶，以檢查一次，它會使用[CSemaphore](../mfc/reference/csemaphore-class.md)限制存取三個檢視表物件。 當嘗試檢視的第四個帳戶發生時，應用程式會等候直到前三個視窗關閉，否則便會失敗。 應用程式的帳戶更新時，使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)以確保只有一個帳戶會更新一次。 更新成功之後，它會通知[CEvent](../mfc/reference/cevent-class.md)，其中釋放執行緒等待事件發出信號。 此執行緒會將新的資料傳送至資料封存。  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 設計安全執行緒類別  
 若要讓類別完全安全的執行緒，先將適當的同步處理類別加入共用的類別做為資料成員。 在上一個帳戶管理範例中， **CSemaphore**資料成員會加入至檢視類別，`CCriticalSection`資料成員會加入至連結清單類別，和`CEvent`資料成員會加入至資料儲存類別。  
  
 接下來，加入同步處理所有成員函式呼叫會修改類別中的資料或存取控制的資源。 每個函式，您應該建立[CSingleLock](../mfc/reference/csinglelock-class.md)或[CMultiLock](../mfc/reference/cmultilock-class.md)物件，並且呼叫該物件`Lock`函式。 物件的解構函式的呼叫時之鎖定物件會超出範圍，會終結`Unlock`，釋放資源。 當然，您可以呼叫`Unlock`直接如果您想要。  
  
 設計您的安全執行緒類別以這種方式可讓它使用中的多執行緒應用程式輕鬆地為非安全執行緒類別，但具有較高的安全性等級。 資源的類別封裝的同步處理物件和同步處理存取物件提供完整的安全執行緒程式設計，而不維持同步程式碼的缺點的所有優點。  
  
 下列程式碼範例會示範這個方法所使用的資料成員， `m_CritSection` (型別`CCriticalSection`)、 共用的資源類別中宣告和`CSingleLock`物件。 共用資源的同步處理 (衍生自`CWinThread`) 嘗試藉由建立`CSingleLock`物件使用的位址`m_CritSection`物件。 嘗試鎖定該資源，並取得，共用的物件時執行工作。 工作完成時，資源已藉由呼叫解除鎖定`Unlock`。  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`與其他 MFC 的同步處理類別、 不同並沒有已逾時的鎖定要求的選項。 等候執行緒成為可用為無限。  
  
 這種方法的缺點是不含加入同步處理物件都將稍微低於相同類別的類別。 此外，如果有多個執行緒可能會刪除物件的機會，合併的方法可能並非永遠適用。 在此情況下，最好是維護個別的同步處理物件。  
  
 如需判斷要在不同的情況下使用哪一個同步處理類別的詳細資訊，請參閱[多執行緒： 何時使用同步類別](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。 如需同步處理的詳細資訊，請參閱[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 如需多執行緒 MFC 支援的詳細資訊，請參閱[多執行緒 c + + 和 MFC](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)