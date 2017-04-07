---
title: "CSingleLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CSingleLock class
- threading [MFC], access control
- synchronization objects, access control
- threading [MFC], synchronization
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
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
ms.openlocfilehash: b1efc2daf1c3714446223cc69f9cc2a6a3401173
ms.lasthandoff: 02/24/2017

---
# <a name="csinglelock-class"></a>CSingleLock 類別
代表多執行緒程式用來控制單一資源存取的存取控制機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|建構 `CSingleLock` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|判斷此物件會被鎖定。|  
|[CSingleLock::Lock](#lock)|等候同步處理物件。|  
|[CSingleLock::Unlock](#unlock)|釋放同步物件。|  
  
## <a name="remarks"></a>備註  
 `CSingleLock`沒有基底類別。  
  
 若要使用同步類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您必須建立`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)等候，並釋放同步處理物件的物件。 使用`CSingleLock`如果您只需要等候一次一個物件。 使用**CMultiLock**時有多個物件，您可以使用特定的時間。  
  
 若要使用`CSingleLock`物件，請在受控制的資源類別中呼叫其建構函式內的成員函式。 然後呼叫[IsLocked](#islocked)成員函式來判斷資源是否可用。 如果是，繼續成員函式的其餘部分。 如果資源無法使用時，等候一段指定的時間，釋放資源，或傳回失敗。 使用的資源完成之後，呼叫[Unlock](#unlock)函式在`CSingleLock`物件是使用一次，或允許`CSingleLock`終結物件。  
  
 `CSingleLock`物件需要一個物件衍生自[CSyncObject](../../mfc/reference/csyncobject-class.md)。 這通常是類別的控制的資源資料成員。 如需有關如何使用`CSingleLock`物件，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CSingleLock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="csinglelock"></a>CSingleLock::CSingleLock  
 建構 `CSingleLock` 物件。  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `pObject`  
 若要存取的同步處理物件的指標。 不能是**NULL**。  
  
 `bInitialLock`  
 指定是否一開始嘗試存取提供的物件。  
  
### <a name="remarks"></a>備註  
 此函式通常受控制資源存取成員函式中呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&19;](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 如果與相關聯的物件會決定`CSingleLock`物件為未收到信號 （無法使用）。  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果物件已鎖定。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&20;](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 呼叫此函式來取得存取權提供給同步處理物件所控制的資源`CSingleLock`建構函式。  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 指定等待可用的同步處理物件的時間量 （通知）。 如果**無限**，`Lock`會等到物件收到信號之前傳回。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果在同步物件收到信號，`Lock`會成功傳回，而且執行緒現在擁有的物件。 如果未收到信號同步處理的物件 （無法使用），`Lock`會等候同步物件變成已收到訊號中指定的毫秒數最*dwTimeOut*參數。 如果同步處理物件未不被通知以指定的時間量`Lock`傳回失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&21;](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>CSingleLock::Unlock  
 釋放同步物件所擁有`CSingleLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 要釋放的存取數目。 必須大於 0。 如果指定的數量會導致物件的計數超過最大值，則不會變更計數和函式會傳回**FALSE**。  
  
 `lPrevCount`  
 指向接收同步處理物件的先前計數的變數。 如果**NULL**，就不會傳回上一個計數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫`CSingleLock`的解構函式。  
  
 如果您要釋放號誌的多個存取計數，請使用第二種`Unlock`和指定的存取版本號碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&21;](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMultiLock 類別](../../mfc/reference/cmultilock-class.md)

