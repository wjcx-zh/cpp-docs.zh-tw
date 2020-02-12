---
title: 多執行緒：如何使用 MFC 同步處理類別
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
ms.openlocfilehash: ef76199813de417d2aa57eb7f3f15ae4d2fefc56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140496"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>多執行緒：如何使用 MFC 同步處理類別

線上程之間同步處理資源存取是撰寫多執行緒應用程式時的常見問題。 有兩個或多個執行緒同時存取相同的資料，可能會導致不想要和無法預期的結果。 例如，一個執行緒可能會在另一個執行緒讀取相同結構的內容時，更新結構的內容。 讀取執行緒要接收的資料不明：舊資料、新寫入的資料，或可能是兩者的混合。 MFC 提供一些同步處理和同步處理存取類別，協助解決此問題。 本主題說明可用的類別，以及如何使用它們在一般多執行緒應用程式中建立安全線程的類別。

典型的多執行緒應用程式有一個類別，代表要線上程之間共用的資源。 適當設計的完全安全線程類別不需要您呼叫任何同步處理函式。 所有專案都是在內部處理類別，可讓您專注于如何最佳使用類別，而不是如何使其損毀。 建立完全安全線程類別的有效技巧，是將同步處理類別合併至資源類別。 將同步處理類別合併到共用類別是一個簡單的程式。

例如，建立一個應用程式來維護帳戶的連結清單。 此應用程式允許在個別的視窗中檢查最多三個帳戶，但在任何特定時間只能更新一個帳戶。 當帳戶更新時，更新的資料會透過網路傳送到資料封存。

這個範例應用程式會使用所有三種類型的同步處理類別。 因為它允許一次檢查最多三個帳戶，所以它會使用[CSemaphore](../mfc/reference/csemaphore-class.md)來限制對三個 view 物件的存取。 當嘗試查看第四個帳戶時，應用程式會等待前三個視窗中的其中一個關閉或失敗。 當帳戶更新時，應用程式會使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)來確保一次只會更新一個帳戶。 更新成功之後，它會發出信號給[CEvent](../mfc/reference/cevent-class.md)，這會釋放等待事件信號的執行緒。 此執行緒會將新的資料傳送至資料封存。

## <a name="_mfc_designing_a_thread.2d.safe_class"></a>設計安全線程類別

若要讓類別具備完整執行緒安全，請先將適當的同步處理類別加入至共用類別做為資料成員。 在先前的帳戶管理範例中，`CSemaphore` 資料成員會加入至 view 類別，`CCriticalSection` 的資料成員會加入至連結的清單類別，而 `CEvent` 資料成員則會加入至資料儲存類別。

接下來，將同步處理呼叫加入至所有成員函式，這些函式會修改類別中的資料，或存取受控制的資源。 在每個函式中，您應該建立[CSingleLock](../mfc/reference/csinglelock-class.md)或[CMultiLock](../mfc/reference/cmultilock-class.md)物件，並呼叫該物件的 `Lock` 函數。 當鎖定物件超出範圍並終結時，物件的析構函式會為您呼叫 `Unlock`，以釋放資源。 當然，您可以視需要直接呼叫 `Unlock`。

以這種方式設計您的執行緒安全類別，可讓它在多執行緒應用程式中輕易地用來做為非安全線程的類別，但具有較高的安全性層級。 將同步處理物件和同步處理存取物件封裝到資源的類別中，可提供完全安全線程程式設計的所有優點，而不需要維護同步處理常式代碼的缺點。

下列程式碼範例會使用在共用資源類別中宣告的資料成員 `m_CritSection` （屬於類型 `CCriticalSection`）來示範這個方法，以及 `CSingleLock` 物件。 使用 `m_CritSection` 物件的位址建立 `CSingleLock` 物件，即可嘗試同步處理共用資源（衍生自 `CWinThread`）。 嘗試鎖定資源，並在取得時，于共用物件上執行工作。 當工作完成時，會使用 `Unlock`的呼叫來解除鎖定資源。

```cpp
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> 與其他 MFC 同步處理類別不同的是，`CCriticalSection`沒有計時鎖定要求的選項。 執行緒變成可用的等候期間是無限的。

這種方法的缺點是，類別會稍微慢于不會加入同步處理物件的相同類別。 此外，如果有一個以上的執行緒可能會刪除物件，則合併的方法可能不一定會有作用。 在此情況下，最好是維護個別的同步處理物件。

如需判斷要在不同情況下使用哪個同步處理類別的詳細資訊，請參閱[多執行緒：何時使用同步類別](multithreading-when-to-use-the-synchronization-classes.md)。 如需同步處理的詳細資訊，請參閱 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)處理。 如需 MFC 中多執行緒支援的詳細資訊，請參閱[使用和 MFC 進行C++多執行緒處理](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
