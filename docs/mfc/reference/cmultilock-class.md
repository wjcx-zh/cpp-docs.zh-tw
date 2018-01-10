---
title: "CMultiLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs: C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dc3c391c624351b2835e1ec497d78bc191eb1fe7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmultilock-class"></a>CMultiLock 類別
代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|建構 `CMultiLock` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|決定是否陣列中的特定同步處理物件已被鎖定。|  
|[CMultiLock::Lock](#lock)|會等候同步處理物件陣列。|  
|[CMultiLock::Unlock](#unlock)|釋放任何擁有同步處理物件。|  
  
## <a name="remarks"></a>備註  
 `CMultiLock`沒有基底類別。  
  
 若要使用同步處理類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您可以建立**CMultiLock**或[CSingleLock](../../mfc/reference/csinglelock-class.md)等候，並釋出同步處理物件的物件。 使用**CMultiLock**時您可以使用在特定時間的多個物件。 使用`CSingleLock`您可能只需要一次等候上一個物件。  
  
 若要使用**CMultiLock**物件，請先建立您想要等候的同步處理物件的陣列。 接下來，呼叫**CMultiLock**內受控制的資源類別中的成員函式物件的建構函式。 然後呼叫[鎖定](#lock)成員函式來判斷是否有可用的資源 （發出訊號）。 如果其中一個，請繼續此成員函式的其餘部分。 如果沒有資源可用，請等候一段指定時間的資源釋出，或傳回失敗。 使用資源已完成之後，呼叫[Unlock](#unlock)函式如果**CMultiLock**物件是使用一次，或允許**CMultiLock**物件也將被銷毀。  
  
 **CMultiLock**時執行緒有大量的物件都是最有用`CEvent`它可以回應的物件。 建立陣列，其中包含所有`CEvent`指標，並呼叫`Lock`。 這會造成執行緒等候，直到其中一個事件發出信號。  
  
 如需有關如何使用**CMultiLock**物件，請參閱文章[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CMultiLock`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmt.h  
  
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
 若要在等候同步處理物件的指標的陣列。 不能**NULL**。  
  
 `dwCount`  
 中的物件數目`ppObjects`。 必須大於 0。  
  
 `bInitialLock`  
 指定是否一開始嘗試存取的任何提供的物件。  
  
### <a name="remarks"></a>備註  
 建立同步處理至等候中的物件陣列之後，會呼叫此函數。 它通常稱為從內必須等候其中一個同步處理物件變成可用的執行緒。  
  
##  <a name="islocked"></a>CMultiLock::IsLocked  
 判斷指定的物件是否為未收到信號 （無法使用）。  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>參數  
 *dwItem*  
 要查詢其狀態的物件相對應的物件陣列中的索引。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果指定的物件已鎖定。否則便是 0。  
  
##  <a name="lock"></a>CMultiLock::Lock  
 呼叫此函式來存取一或多個資源提供給同步處理物件所控制的**CMultiLock**建構函式。  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 指定等待可用的同步處理物件的時間量 （發出訊號）。 如果**無限**，`Lock`會等候，直到物件傳回之前收到信號。  
  
 `bWaitForAll`  
 指定是否必須在相同的時間傳回前被通知所有等候的物件。 如果**FALSE**，`Lock`等候任何的物件一個為收到信號時，會傳回。  
  
 `dwWakeMask`  
 指定允許中止等候其他條件。 如需此參數的可用選項的完整清單，請參閱[MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 如果`Lock`失敗，則傳回-1。 如果成功的話，它會傳回下列值之一：  
  
-   之間**WAIT_OBJECT_0**和**WAIT_OBJECT_0** + （數字的物件-1）  
  
     如果`bWaitForAll`是**TRUE**，所有物件都收到都信號 （可用）。 如果`bWaitForAll`是**FALSE**，傳回值- **WAIT_OBJECT_0**為收到信號物件之物件的陣列中的索引 （可用）。  
  
- **WAIT_OBJECT_0** + （數字的物件）  
  
     指定事件`dwWakeMask`可用執行緒的輸入佇列中。  
  
-   之間**WAIT_ABANDONED_0**和**WAIT_ABANDONED_0** + （數字的物件-1）  
  
     如果`bWaitForAll`是**TRUE**、 所有物件都收到都信號，且至少其中一個物件的已放棄的 mutex 物件。 如果`bWaitForAll`是**FALSE**，傳回值- **WAIT_ABANDONED_0**已放棄的 mutex 物件滿足等候條件之物件的陣列中的索引。  
  
- **WAIT_TIMEOUT**  
  
     中指定的逾時間隔*dwTimeOut*過期但不等候成功。  
  
### <a name="remarks"></a>備註  
 如果`bWaitForAll`是**TRUE**，`Lock`變成同時收到訊號的同步處理的所有物件時將會成功傳回。 如果`bWaitForAll`是**FALSE**，`Lock`將傳回，因為一或多個同步處理物件發出信號。  
  
 如果`Lock`無法立即傳回，它將會等候中指定的毫秒數個以內*dwTimeOut*傳回之前的參數。 如果*dwTimeOut*是**無限**，`Lock`取得物件的存取權時，或在指定的條件之前，不會傳回`dwWakeMask`符合。 否則，如果`Lock`已能夠取得同步處理物件，它會傳回成功; 如果沒有，它會傳回失敗。  
  
##  <a name="unlock"></a>CMultiLock::Unlock  
 釋放所擁有之同步處理物件`CMultiLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 釋放計算參考的數目。 必須大於 0。 如果指定的數量會導致超過最大值的物件的計數，計數不會變更，並傳回函式**FALSE**。  
  
 `lPrevCount`  
 指向接收之同步處理物件的先前計數的變數。 如果**NULL**，就不會傳回前次計數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 會呼叫此函式`CMultiLock`的解構函式。  
  
 第一種形式的`Unlock`嘗試解除鎖定受同步處理物件`CMultiLock`。 第二種`Unlock`嘗試解除鎖定`CSemaphore`擁有的物件`CMultiLock`。 如果`CMultiLock`未擁有任何鎖定`CSemaphore`物件，此函數會傳回**FALSE**; 否則它會傳回**TRUE**。 `lCount`和`lpPrevCount`並完全相同的參數[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二種`Unlock`很少用於 multilock 的情況。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)



