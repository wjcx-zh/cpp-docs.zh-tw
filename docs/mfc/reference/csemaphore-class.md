---
title: "CSemaphore 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, semaphores
- CSemaphore class
- semaphores
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 31de1e553ea2facea6b70c284aecdbf10e22c89f
ms.lasthandoff: 02/24/2017

---
# <a name="csemaphore-class"></a>CSemaphore 類別
類別的物件`CSemaphore`表示 「 號誌 」 — 允許有限的數量的執行緒在存取持續的一或多個處理序目前存取指定的資源的執行緒數目的計數的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|建構 `CSemaphore` 物件。|  
  
## <a name="remarks"></a>備註  
 號誌是用於控制僅支援有限的使用者共用資源的存取權。 目前的計數`CSemaphore`物件是允許其他使用者的數目。 當計數到達零時，所有嘗試使用受到資源**CSemaphore**物件就會插入到系統佇列，等到他們其中一個逾時時間或計數超過 0。 可以一次存取控制的資源的使用者數目上限在建構期間指定`CSemaphore`物件。  
  
 若要使用**CSemaphore**物件，建構`CSemaphore`物件會在需要時。 指定您想要等候，號誌的名稱和您的應用程式一開始應該擁有它。 然後，建構函式傳回時，您可以存取之號誌。 呼叫[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成存取控制的資源。  
  
 使用替代方法`CSemaphore`物件是新增型別的變數`CSemaphore`以您想要控制的類別資料成員。 在受控制的物件建構期間呼叫的建構函式`CSemaphore`指定初始資料成員存取計數、 最高存取權的計數、 號誌 （如果它將會使用跨處理序界限） 的名稱和所需的安全性屬性。  
  
 控制存取資源`CSemaphore`物件以這種方式，先建立這兩種類型的變數[CSingleLock](../../mfc/reference/csinglelock-class.md)或型別[CMultiLock](../../mfc/reference/cmultilock-class.md)在您的資源存取的成員函式。 接著呼叫鎖定物件的`Lock`成員函式 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此時，您的執行緒會取得資源的存取權，等待資源釋出，並存取應用程式，或等待資源釋出及逾時，無法存取的資源。 在任何情況下，您的資源已存取具備執行緒安全的方式。 若要釋放資源，使用鎖定物件的`Unlock`成員函式 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允許超出範圍的鎖定物件。  
  
 或者，您可以建立**CSemaphore**物件獨立存在，並明確再嘗試存取控制的資源存取。 這個方法，同時清楚給其他人讀取程式碼中，是更容易發生錯誤。  
  
 如需有關如何使用**CSemaphore**物件，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="a-namecsemaphorea--csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore  
 建構具名或未命名的`CSemaphore`物件。  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lInitialCount*  
 號誌的初始的使用方式計數。 必須是大於或等於 0，且小於或等於`lMaxCount`。  
  
 `lMaxCount`  
 號誌的最大使用量計數。 必須大於 0。  
  
 `pstrName`  
 號誌的名稱。 如果存取號誌的跨處理序界限，必須提供。 如果`NULL,`物件將會是未命名。 如果名稱符合現有的號誌，建構函式會建置新`CSemaphore`會參考該名稱的號誌的物件。 如果名稱符合現有的同步處理物件不是號誌，建構將會失敗。  
  
 *lpsaAttributes*  
 號誌物件的安全性屬性。 此結構的完整說明，請參閱[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 存取或釋放`CSemaphore`物件，請建立[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)物件，然後呼叫其[鎖定](../../mfc/reference/csinglelock-class.md#lock)和[Unlock](../../mfc/reference/csinglelock-class.md#unlock)成員函式。  
  
> [!IMPORTANT]
>  在建立之後`CSemaphore`物件，請使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以確保，mutex 原本不存在。 如果存在非預期地 mutex，可能表示處理序佔用，而且可能會想要進行惡意使用 mutex。 在此情況下，建議的注重安全性的程序是關閉此控制代碼，並繼續如同在建立物件時發生錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [CSyncObject 類別](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




