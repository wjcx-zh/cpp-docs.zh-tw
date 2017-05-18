---
title: "CSyncObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject class
- synchronization classes, CSyncObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a1f0c8ddfbfaf129bb18c14d36b998dd37d35899
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="csyncobject-class"></a>CSyncObject 類別
在 Win32 中提供同步處理物件常見功能的純虛擬類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CSyncObject : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](#csyncobject)|建構 `CSyncObject` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|而同步處理物件的存取。|  
|[CSyncObject::Unlock](#unlock)|而同步處理物件的存取。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CSyncObject::operator 控制代碼](#operator_handle)|提供同步處理物件的存取權。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|基礎的同步處理物件的控制代碼。|  
  
## <a name="remarks"></a>備註  
 Mfc 程式庫提供數個類別衍生自`CSyncObject`。 這些是[CEvent](../../mfc/reference/cevent-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 如需如何使用同步處理物件的資訊，請參閱文章[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmt.h  
  
##  <a name="csyncobject"></a>CSyncObject::CSyncObject  
 建構的同步處理物件，使用提供的名稱。  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>參數  
 `pstrName`  
 物件的名稱。 如果**NULL**， *pstrName*將會是 null。  
  
##  <a name="lock"></a>CSyncObject::Lock  
 呼叫此函式可存取由同步處理物件所控制的資源。  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `dwTimeout`  
 以毫秒為單位所等待的同步處理物件，可指定的時間量 （通知）。 如果**無限**，`Lock`會等到物件收到信號之前傳回。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果在同步物件收到信號，`Lock`會成功傳回，而且執行緒現在擁有的物件。 如果未收到信號同步處理的物件 （無法使用），`Lock`會等候同步物件變成已收到訊號中指定的毫秒數最*dwTimeOut*參數。 如果同步處理物件未不被通知以指定的時間量`Lock`傳回失敗。  
  
##  <a name="m_hobject"></a>CSyncObject::m_hObject  
 基礎的同步處理物件的控制代碼。  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="operator_handle"></a>CSyncObject::operator 控制代碼  
 若要取得的控制代碼使用這個運算子`CSyncObject`物件。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，同步處理物件; 的控制代碼否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 若要直接呼叫 Windows Api，您可以使用控制代碼。  
  
##  <a name="unlock"></a>CSyncObject::Unlock  
 宣告`Unlock`不含任何參數是純虛擬函式，並且必須被覆寫的所有類別衍生自`CSyncObject`。  
  
```  
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,  
    LPLONG lpPrevCount = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 不使用預設的實作。  
  
 `lpPrevCount`  
 不使用預設的實作。  
  
### <a name="return-value"></a>傳回值  
 預設實作一定會傳回**TRUE**。  
  
### <a name="remarks"></a>備註  
 預設實作的兩個參數的宣告永遠會傳回**TRUE**。 您可以呼叫此函式釋放同步物件呼叫的執行緒所擁有的存取權。 第二個宣告可供同步處理物件，例如允許多個存取控制的資源中的號誌。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




