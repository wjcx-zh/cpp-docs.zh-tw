---
title: CSyncObject 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1712f0d26fc0d9ac3dcfb0f2a15a906351f43154
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374093"
---
# <a name="csyncobject-class"></a>CSyncObject 類別
在 Win32 中提供同步處理物件常見功能的純虛擬類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CSyncObject : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](#csyncobject)|建構 `CSyncObject` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|提升的存取權之同步處理物件。|  
|[CSyncObject::Unlock](#unlock)|提升的存取權之同步處理物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSyncObject::operator 控制代碼](#operator_handle)|提供存取同步處理物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|基礎的同步處理物件的控制代碼。|  
  
## <a name="remarks"></a>備註  
 Microsoft Foundation 類別庫會提供數個類別衍生自`CSyncObject`。 這些是[CEvent](../../mfc/reference/cevent-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 如需如何使用同步處理物件的資訊，請參閱文章[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmt.h  
  
##  <a name="csyncobject"></a>  CSyncObject::CSyncObject  
 建構具有所提供名稱的同步處理物件。  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>參數  
 `pstrName`  
 物件的名稱。 如果**NULL**， *pstrName*將會是 null。  
  
##  <a name="lock"></a>  CSyncObject::Lock  
 呼叫此函式可存取由同步處理物件所控制的資源。  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>參數  
 `dwTimeout`  
 以毫秒為單位，等候同步處理物件，才能使用指定的時間量 （發出訊號）。 如果**無限**，`Lock`會等候，直到物件傳回之前收到信號。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果在同步處理物件收到信號，`Lock`會成功傳回，而執行緒現在擁有的物件。 如果同步處理的物件未收到信號 （無法使用）`Lock`會等候同步處理物件發出訊號的中指定的毫秒數最*dwTimeOut*參數。 如果同步處理物件未不會被通知指定一段時間內，`Lock`傳回失敗。  
  
##  <a name="m_hobject"></a>  CSyncObject::m_hObject  
 基礎的同步處理物件的控制代碼。  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="operator_handle"></a>  CSyncObject::operator 控制代碼  
 使用此運算子，來取得控制代碼`CSyncObject`物件。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，與同步處理物件的控制代碼否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 您可以直接呼叫 Windows Api 中使用控制代碼。  
  
##  <a name="unlock"></a>  CSyncObject::Unlock  
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
 預設實作的兩個參數宣告一律會傳回**TRUE**。 您可以呼叫此函式釋放呼叫的執行緒所擁有的同步處理物件的存取權。 第二個宣告提供同步處理物件，例如號誌，可讓多個受控制資源的存取。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



