---
title: CSingleLock 類別 |Microsoft 文件
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
ms.openlocfilehash: 1ae72b7c9c2acf4fa8600903061869ba049cd58c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[CSingleLock::IsLocked](#islocked)|決定是否物件已鎖定。|  
|[CSingleLock::Lock](#lock)|會等候同步處理物件。|  
|[CSingleLock::Unlock](#unlock)|釋放的同步處理物件。|  
  
## <a name="remarks"></a>備註  
 `CSingleLock` 沒有基底類別。  
  
 若要使用同步類別[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您必須建立`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)等候，並釋出同步處理物件的物件。 使用`CSingleLock`您可能只需要一次等候上一個物件。 使用**CMultiLock**時您可以使用在特定時間的多個物件。  
  
 若要使用`CSingleLock`物件，在受控制的資源類別中呼叫其建構函式內的成員函式。 然後呼叫[IsLocked](#islocked)成員函式來判斷資源是否可用。 如果是，繼續進行此成員函式的其餘部分。 如果資源無法使用，請等候一段指定時間的資源釋出，或傳回失敗。 使用的資源已完成之後，呼叫[Unlock](#unlock)函式如果`CSingleLock`物件是使用一次，或允許`CSingleLock`物件也將被銷毀。  
  
 `CSingleLock` 物件，可能需要的衍生自物件存在[CSyncObject](../../mfc/reference/csyncobject-class.md)。 這通常是類別的控制的資源資料成員。 如需有關如何使用`CSingleLock`物件，請參閱文章[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
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
 `pObject`  
 指向要存取的同步處理物件。 不能**NULL**。  
  
 `bInitialLock`  
 指定是否一開始嘗試存取提供的物件。  
  
### <a name="remarks"></a>備註  
 此函式通常受控制的資源存取成員函式中呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>  CSingleLock::IsLocked  
 如果與相關聯的物件會判斷`CSingleLock`物件為未收到信號 （無法使用）。  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果物件已鎖定。否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>  CSingleLock::Lock  
 呼叫此函式可取得存取權提供給同步處理物件所控制的資源`CSingleLock`建構函式。  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>參數  
 *dwTimeOut*  
 指定等待可用的同步處理物件的時間量 （發出訊號）。 如果**無限**，`Lock`會等候，直到物件傳回之前收到信號。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果在同步處理物件收到信號，`Lock`會成功傳回，而執行緒現在擁有的物件。 如果同步處理的物件未收到信號 （無法使用）`Lock`會等候同步處理物件發出訊號的中指定的毫秒數最*dwTimeOut*參數。 如果同步處理物件未不會被通知指定一段時間內，`Lock`傳回失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>  CSingleLock::Unlock  
 釋放所擁有之同步處理物件`CSingleLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 要釋放的存取數目。 必須大於 0。 如果指定的數量會導致超過最大值的物件的計數，計數不會變更，並傳回函式**FALSE**。  
  
 `lPrevCount`  
 指向接收之同步處理物件的先前計數的變數。 如果**NULL**，就不會傳回前次計數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 會呼叫此函式`CSingleLock`的解構函式。  
  
 如果您要釋放號誌的多個存取計數，請使用第二種`Unlock`並指定要發行的存取數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMultiLock 類別](../../mfc/reference/cmultilock-class.md)
