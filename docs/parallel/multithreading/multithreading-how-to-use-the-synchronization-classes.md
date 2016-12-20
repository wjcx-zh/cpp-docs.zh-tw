---
title: "多執行緒：如何使用同步類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], 多執行緒"
  - "多執行緒 [C++], 同步類別"
  - "資源 [C++], 多執行緒"
  - "同步 [C++], 多執行緒"
  - "同步類別 [C++]"
  - "執行緒 [C++], 同步"
  - "執行緒 [C++], 安全執行緒類別設計"
  - "執行緒 [MFC], 同步類別"
  - "執行緒 [MFC], 安全執行緒類別設計"
  - "安全執行緒類別 [C++]"
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：如何使用同步類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在執行緒之間同步存取資源是在撰寫多執行緒應用程式時常見的問題。  讓兩個或更多的執行緒同時存取相同的資料，可能會造成不希望發生和無法預期的結果。  例如，一個執行緒更新結構的內容時，另一個執行緒讀取相同結構的內容。  無法得知讀取的執行緒會收到什麼樣的資料：舊資料、新撰寫的資料或兩者的混合。  MFC 提供一些同步作業和同步存取類別來協助解決這個問題。  這個主題說明在一般多執行緒應用程式中可用的類別，以及如何使用它們來建立安全執行緒 \(Thread\-safe\) 的類別。  
  
 一般多執行緒應用程式擁有代表執行緒之間共用資源的類別。  正確設計而且完整的安全執行緒類別不需要您呼叫任何的同步函式。  每件事都是由類別內部處理，可讓您專注於如何好好利用類別，而不是專注於如何避免類別遭到損毀。  建立完整安全執行緒類別的有效技術，就是將同步類別合併至資源類別。  將同步類別合併到共用類別是直接的程序。  
  
 例如，取得維護帳戶之連結串列的應用程式。  這個帳戶最多允許在不同視窗中查看三個帳戶，但一次只能有一個可以被更新。  當更新帳戶時，更新的資料會經由網路傳送到資料保存。  
  
 這個範例使用全部三種同步類別。  因為它最多允許同時查看三個帳戶，並使用 [CSemaphore](../../mfc/reference/csemaphore-class.md) 來限制三個檢視物件的存取。  嘗試檢視第四個帳戶時，應用程式會等候前三個視窗其中之一關閉，否則便會失敗。  更新帳戶時，應用程式使用 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md) 來確保一次只更新一個帳戶。  更新成功之後，會發送信號至 [CEvent](../../mfc/reference/cevent-class.md)，以釋放等候被發送信號之事件的執行緒。  這個執行緒會將新資料傳送到資料保存。  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 設計安全執行緒類別  
 若要讓類別成為完整的安全執行緒，首先將適當的同步類別加入至共用類別當做資料成員。  在上述帳戶管理範例中，**CSemaphore** 資料成員會被加入至檢視類別，`CCriticalSection` 資料成員會被加入至連結串列類別，而 `CEvent` 資料成員會被加入至資料儲存類別。  
  
 接著，將同步作業呼叫加入至會修改類別內資料或存取控制資源的所有成員 \(Member\) 函式。  在每個函式中，您應該建立 [CSingleLock](../../mfc/reference/csinglelock-class.md) 或 [CMultiLock](../../mfc/reference/cmultilock-class.md) 物件，並且呼叫該物件的 `Lock` 函式。  當鎖定物件離開範圍並且被終結時，物件的解構函式會為您呼叫 `Unlock` 釋放資源。  當然，如果您要的話，可以直接呼叫 `Unlock`。  
  
 以這種方式設計您的安全執行緒類別，可讓它在使用於多執行緒應用程式時，就像設計非安全執行緒類別一樣簡單，而且具有較高的安全性層級。  將同步作業物件和同步存取物件封裝到資源的類別中，會提供完整安全執行緒程式設計的所有優點，而沒有維持同步程式碼的缺點。  
  
 下列程式碼範例藉著使用在共用資源類別和 `CSingleLock` 物件中的資料成員 `m_CritSection` \(屬於 `CCriticalSection` 型別\) 來示範這種方法。  共用資源的同步作業 \(衍生自 `CWinThread` \) 是藉著使用 `m_CritSection` 物件的位址來建立 `CSingleLock` 物件來被嘗試。  會嘗試鎖定資源，並且在取得之後完成共用物件的工作。  一旦工作完成後，會使用呼叫 `Unlock` 來解除鎖定資源。  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  與其他的 MFC 同步類別不一樣，`CCriticalSection` 沒有計時鎖定要求的選項。  等候執行緒變成自由的時間是無限。  
  
 這種方法的缺點是這個類別會比沒有加入同步物件的相同類別稍微慢一點。  同時，如果有一個以上的執行緒可能會刪除物件的機會，則合併的方法就不一定總是有用。  在這種情況下，最好維持分開的同步物件。  
  
 如需決定在何種情況下使用哪個同步類別的詳細資訊，請參閱[多執行緒：何時使用同步類別](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  如需同步處理的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  如需 MFC 多執行緒支援的詳細資訊，請參閱[使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)