---
title: CSingleLock 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 3d9b418e5f8aafc4199712063e137aadc9df04f3
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852435"
---
# <a name="csinglelock-class"></a>CSingleLock 類別
代表多執行緒程式用來控制單一資源存取的存取控制機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|建構 `CSingleLock` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|判斷此物件會被鎖定。|  
|[CSingleLock::Lock](#lock)|會等候同步處理物件。|  
|[CSingleLock::Unlock](#unlock)|釋放同步物件。|  
  
## <a name="remarks"></a>備註  
 `CSingleLock` 沒有基底類別。  
  
 若要使用同步類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，以及[CEvent](../../mfc/reference/cevent-class.md)，您必須建立`CSingleLock`或是[CMultiLock](../../mfc/reference/cmultilock-class.md)等候，並釋放同步物件的物件。 使用`CSingleLock`您可能只需要等候上一個物件一次。 使用`CMultiLock`時有多個物件，您可以使用特定的時間。  
  
 若要使用`CSingleLock`物件，請在受控制的資源類別中呼叫其建構函式內的成員函式。 然後呼叫[IsLocked](#islocked)成員函式來判斷資源是否可用。 如果是，繼續進行此成員函式的其餘部分。 如果資源無法使用時，等候指定的發行，資源的時間量，或傳回失敗。 使用的資源完成之後，呼叫[Unlock](#unlock)函式`CSingleLock`物件是使用一次，或允許`CSingleLock`来終結物件。  
  
 `CSingleLock` 物件，可能需要從衍生的物件是否存在[CSyncObject](../../mfc/reference/csyncobject-class.md)。 這通常是受控制的資源類別的資料成員。 如需有關如何使用`CSingleLock`物件，請參閱文章[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CSingleLock`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmt.h  
  
##  <a name="csinglelock"></a>  CSingleLock::CSingleLock  
 建構 `CSingleLock` 物件。  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *pObject*  
 若要存取的同步處理物件的點。 不可以是 NULL。  
  
 *bInitialLock*  
 指定是否一開始嘗試存取提供的物件。  
  
### <a name="remarks"></a>備註  
 從受控制的資源的存取成員函式內通常呼叫此函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>  CSingleLock::IsLocked  
 如果與相關聯的物件會判斷`CSingleLock`物件是未收到信號 （無法使用）。  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件已鎖定，則為非零否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>  CSingleLock::Lock  
 呼叫此函式來取得存取權提供給同步處理物件所控制的資源`CSingleLock`建構函式。  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 指定要同步處理物件可等候的時間量 （發出訊號）。 如果是無限的`Lock`會等候，直到物件收到信號之前傳回。  
  
### <a name="return-value"></a>傳回值  
 如果函式時成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果在同步物件收到信號，`Lock`成功會傳回與執行緒現在擁有的物件。 如果未收到信號之同步處理物件 （無法使用），`Lock`會等候同步處理物件變成已收到訊號的中指定的毫秒數最*dwTimeOut*參數。 如果同步處理物件未變成收到訊號在指定的時間內，`Lock`傳回失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>  CSingleLock::Unlock  
 釋放所擁有的同步處理物件`CSingleLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lCount*  
 要釋放的存取數目。 必須大於 0。 如果指定的數量會導致超過其最大值的物件的計數，計數不會變更，而且函式會傳回 FALSE。  
  
 *lPrevCount*  
 指向接收之同步處理物件的先前計數的變數。 如果是 NULL，不會傳回上一個計數。  
  
### <a name="return-value"></a>傳回值  
 如果函式時成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫`CSingleLock`的解構函式。  
  
 如果您要釋放號誌的多個存取計數時，使用的第二個形式`Unlock`並指定要釋放的存取數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMultiLock 類別](../../mfc/reference/cmultilock-class.md)
