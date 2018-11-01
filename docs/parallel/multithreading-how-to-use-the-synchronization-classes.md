---
title: 多執行緒： 如何使用 MFC 的同步處理類別
ms.date: 08/27/2018
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
ms.openlocfilehash: 0f8304c3b45f87dadc2317de95a0b30b54baffa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604161"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>多執行緒： 如何使用 MFC 的同步處理類別

撰寫多執行緒應用程式時，同步處理執行緒之間的資源存取權是常見的問題。 有兩個或多個執行緒同時存取相同的資料可能會導致非預期且無法預測的結果。 例如，一個執行緒可能在更新結構的內容而另一個執行緒正在讀取相同結構的內容。 它是未知資料讀取執行緒將會收到： 舊的資料、 新寫入的資料，或可能是兩者的混合。 MFC 提供許多同步處理和同步存取類別，以協助解決此問題。 本主題會說明可用的類別，以及如何使用它們來建立安全執行緒類別在典型的多執行緒應用程式中。

典型的多執行緒應用程式具有的類別，代表在執行緒之間共用的資源。 設計得當，完整的安全執行緒類別不需要呼叫任何同步處理函式。 至類別，可讓您專注於如何充分利用的類別，不需可能會損毀它如何在內部處理所有項目。 建立完整的安全執行緒類別的有效技術是合併的資源類別中的同步處理類別。 同步類別合併至共用的類別是簡單的程序。

例如，擷取應用程式維護帳戶的連結的清單。 此應用程式可讓最多三個帳戶，以在個別的視窗中加以檢查，但只有一個可以更新任何特定的時間。 更新帳戶時，更新的資料是透過網路傳送至資料封存。

此範例應用程式會使用三種同步處理的類別。 因為它可讓要檢查一次最多三個帳戶，它會使用[CSemaphore](../mfc/reference/csemaphore-class.md)限制三個檢視物件的存取權。 當嘗試檢視的第四個帳戶時，就會等候直到其中一個第三個視窗關閉或失敗的應用程式。 應用程式的帳戶更新時，使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)來確保只有一個帳戶會更新一次。 更新成功之後，它會通知[CEvent](../mfc/reference/cevent-class.md)，這會釋放執行緒等待事件收到訊號。 此執行緒會將新的資料傳送至資料封存。

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 設計安全執行緒類別

若要讓類別成為完整的安全執行緒，先將適當的同步處理類別加入共用的類別做為資料成員。 在先前的帳戶管理範例中，`CSemaphore`資料成員都會新增至檢視類別`CCriticalSection`資料成員會加入至連結清單類別，和`CEvent`資料成員會加入至資料儲存體類別。

接下來，新增所有成員函式可修改的類別中的資料，或存取控制的資源的同步處理呼叫。 在每個函式中，您應該建立其中一個[CSingleLock](../mfc/reference/csinglelock-class.md)或是[CMultiLock](../mfc/reference/cmultilock-class.md)物件，並呼叫該物件的`Lock`函式。 當鎖定物件會超出範圍，並且被終結時，物件的解構函式呼叫`Unlock`，釋放資源。 當然，您可以呼叫`Unlock`直接如果您想要。

設計您的安全執行緒類別以這種方式可讓它用於多執行緒應用程式輕鬆地為非安全執行緒類別，但具有較高層級的安全性。 將同步處理物件和同步處理存取物件封裝成資源的類別提供完整的安全執行緒程式設計，而不需要維護的同步處理程式碼的缺點的所有優點。

下列程式碼範例會示範這個方法所使用的資料成員`m_CritSection`(型別的`CCriticalSection`)、 共用的資源類別中宣告和`CSingleLock`物件。 共用資源的同步處理 (衍生自`CWinThread`) 會嘗試藉由建立`CSingleLock`物件使用的位址`m_CritSection`物件。 嘗試鎖定該資源，並取得，工作會對共用的物件。 工作完成時，資源是藉由呼叫解除鎖定`Unlock`。

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`與其他 MFC 的同步處理類別、 不同的是沒有逾時的鎖定要求的選項。 等候執行緒變成可用的等待時間是無限的。

這種方法的缺點是，類別會稍微慢一點比相同的類別而不需要加入同步處理物件。 此外，如果有多個執行緒可能會刪除物件的機會，合併的方法可能無法永遠運作。 在此情況下，最好是維護個別的同步處理物件。

如需判斷要在不同的情況下使用的同步處理類別的詳細資訊，請參閱 <<c0> [ 多執行緒： 何時使用同步類別](multithreading-when-to-use-the-synchronization-classes.md)。 如需有關同步處理的詳細資訊，請參閱 <<c0> [ 同步處理](/windows/desktop/Sync/synchronization)Windows SDK 中。 如需在 MFC 中的多執行緒支援的詳細資訊，請參閱[c + + 和 MFC 的多執行緒](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)