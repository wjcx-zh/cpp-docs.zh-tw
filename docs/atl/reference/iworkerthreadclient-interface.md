---
title: "IWorkerThreadClient 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IWorkerThreadClient
- ATL::IWorkerThreadClient
- IWorkerThreadClient
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: 24
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2127d13dc11edb353ef27396f3457dd9abdc4a99
ms.lasthandoff: 02/24/2017

---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 介面
`IWorkerThreadClient`是用戶端所實作的介面[CWorkerThread](../../atl/reference/cworkerthread-class.md)類別。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|實作這個方法，以關閉此物件相關聯的控制代碼。|  
|[執行](#execute)|實作這個方法與這個物件相關聯的控制代碼會變成已收到訊號時執行程式碼。|  
  
## <a name="remarks"></a>備註  
 當您需要在變成已收到訊號的控制代碼的回應中，工作者執行緒上執行的程式碼時，請實作這個介面。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="a-nameclosehandlea--iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 實作這個方法，以關閉此物件相關聯的控制代碼。  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>參數  
 *hHandle*  
 若要關閉控制代碼。  
  
### <a name="return-value"></a>傳回值  
 成功或失敗的錯誤 HRESULT 會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 傳遞至這個方法的控制代碼未與此物件呼叫先前關聯[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼顯示的簡單實作`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities #&135;](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="a-nameexecutea--iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Execute  
 實作這個方法與這個物件相關聯的控制代碼會變成已收到訊號時執行程式碼。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>參數  
 `dwParam`  
 User 參數。  
  
 `hObject`  
 變成已收到訊號的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 成功或失敗的錯誤 HRESULT 會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼和 DWORD/指標傳遞給這個方法已與此物件的呼叫之前相關[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼顯示的簡單實作`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities #&136;](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)

