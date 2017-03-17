---
title: "CMultiLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock class
- synchronization objects, access control
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
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
ms.openlocfilehash: a58d59d8e4d7a1c542dee80295dd8eef6c8be338
ms.lasthandoff: 02/24/2017

---
# <a name="cmultilock-class"></a>CMultiLock 類別
代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|建構 `CMultiLock` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|決定是否陣列中的特定同步處理物件已被鎖定。|  
|[CMultiLock::Lock](#lock)|會等候同步處理物件的陣列。|  
|[CMultiLock::Unlock](#unlock)|釋放任何擁有同步處理物件。|  
  
## <a name="remarks"></a>備註  
 `CMultiLock`沒有基底類別。  
  
 若要使用同步類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您可以建立**CMultiLock**或[CSingleLock](../../mfc/reference/csinglelock-class.md)等候，並釋放同步處理物件的物件。 使用**CMultiLock**時有多個物件，您可以使用特定的時間。 使用`CSingleLock`如果您只需要等候一次一個物件。  
  
 若要使用**CMultiLock**物件，請先建立您想要等候的同步處理物件的陣列。 接下來，呼叫**CMultiLock**內控制的資源類別的成員函式物件的建構函式。 然後呼叫[鎖定](#lock)成員函式來判斷資源是否可用 （通知）。 如果有，繼續成員函式的其餘部分。 如果沒有資源可用，請等候一段指定的時間，釋放資源，或傳回失敗。 使用資源完成之後，呼叫[Unlock](#unlock)函式在**CMultiLock**物件是使用一次，或允許**CMultiLock**終結物件。  
  
 **CMultiLock**時執行緒有大量的物件都是最有用`CEvent`它可以回應的物件。 建立陣列，其中包含所有`CEvent`指標，並呼叫`Lock`。 這會造成執行緒等候，直到其中一個事件收到信號。  
  
 如需有關如何使用**CMultiLock**物件，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CMultiLock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="cmultilock"></a>CMultiLock::CMultiLock  
 建構**CMultiLock**物件。  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `ppObjects`  
 若要在等候同步處理物件的指標的陣列。 不能是**NULL**。  
  
 `dwCount`  
 中的物件數目`ppObjects`。 必須大於 0。  
  
 `bInitialLock`  
 指定是否一開始嘗試存取的任何提供的物件。  
  
### <a name="remarks"></a>備註  
 建立等候的同步處理物件的陣列之後，會呼叫此函數。 它通常會從呼叫，必須等待可用的同步處理物件的其中一個執行緒內。  
  
##  <a name="islocked"></a>CMultiLock::IsLocked  
 判斷指定的物件是否為未收到信號 （無法使用）。  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>參數  
 *dwItem*  
 對應至其狀態所查詢之物件的物件的陣列中的索引。  
  
### <a name="return-value"></a>傳回值  
 非零，如果指定的物件已鎖定。否則為 0。  
  
##  <a name="lock"></a>CMultiLock::Lock  
 呼叫此函式來存取一或多個同步處理物件提供給所控制的資源**CMultiLock**建構函式。  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 指定等待可用的同步處理物件的時間量 （通知）。 如果**無限**，`Lock`會等到物件收到信號之前傳回。  
  
 `bWaitForAll`  
 指定是否必須傳回前一次被通知等候中的所有物件。 如果**FALSE**，`Lock`其中一個等候物件收到信號時，會傳回。  
  
 `dwWakeMask`  
 指定允許中止等候其他條件。 這個參數的可用選項的完整清單，請參閱[MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果`Lock`失敗，它會傳回 – 1。 如果成功的話，它會傳回下列值之一︰  
  
-   之間**WAIT_OBJECT_0**和**WAIT_OBJECT_0** + （物件 – 1 的數字）  
  
     如果`bWaitForAll`是**TRUE**，所有物件收到都信號 （可用）。 如果`bWaitForAll`是**FALSE**，傳回的值- **WAIT_OBJECT_0**為收到信號的物件之物件的陣列中的索引 （可用）。  
  
- **WAIT_OBJECT_0** + （數字的物件）  
  
     事件中指定`dwWakeMask`可用執行緒的輸入佇列中。  
  
-   之間**WAIT_ABANDONED_0**和**WAIT_ABANDONED_0** + （物件 – 1 的數字）  
  
     如果`bWaitForAll`是**TRUE**、 所有物件都收到都信號，和至少其中一個物件是放棄的 mutex 物件。 如果`bWaitForAll`是**FALSE**，傳回的值- **WAIT_ABANDONED_0**已放棄的 mutex 物件滿足等候條件之物件的陣列中的索引。  
  
- **WAIT_TIMEOUT**  
  
     中指定的逾時間隔*dwTimeOut*已過期但未等候定址。  
  
### <a name="remarks"></a>備註  
 如果`bWaitForAll`是**TRUE**，`Lock`會為所有同步處理物件變成已收到訊號同時成功傳回。 如果`bWaitForAll`是**FALSE**，`Lock`一或多個同步物件收到信號，會傳回。  
  
 如果`Lock`無法立即傳回，它會等待中指定的毫秒數超過*dwTimeOut*傳回之前的參數。 如果*dwTimeOut*是**無限**，`Lock`獲得存取物件或條件中指定之前將不會傳回`dwWakeMask`符合。 否則，如果`Lock`是無法取得的同步處理物件，它會傳回成功; 如果沒有，它會傳回失敗。  
  
##  <a name="unlock"></a>CMultiLock::Unlock  
 釋放同步物件所擁有`CMultiLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 釋放計算參考的數目。 必須大於 0。 如果指定的數量會導致物件的計數超過最大值，則不會變更計數和函式會傳回**FALSE**。  
  
 `lPrevCount`  
 指向接收同步處理物件的上一個計數的變數。 如果**NULL**，就不會傳回上一個計數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫`CMultiLock`的解構函式。  
  
 第一種形式的`Unlock`嘗試解除鎖定由同步處理物件`CMultiLock`。 第二種`Unlock`嘗試解除鎖定`CSemaphore`擁有的物件`CMultiLock`。 如果`CMultiLock`未擁有任何鎖定`CSemaphore`物件，此函數會傳回**FALSE**; 否則它會傳回**TRUE**。 `lCount`和`lpPrevCount`並完全相同的參數[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二種`Unlock`很少適用於 multilock 的情況。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)




