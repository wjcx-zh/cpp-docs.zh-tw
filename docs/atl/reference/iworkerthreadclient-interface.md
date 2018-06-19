---
title: IWorkerThreadClient 介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8336edb07d02bbbcd5775eaf3ef8fe0f735d3adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359813"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 介面
`IWorkerThreadClient` 是由用戶端的服務所實作的介面[CWorkerThread](../../atl/reference/cworkerthread-class.md)類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|實作這個方法關閉此控制代碼，這個物件相關聯。|  
|[執行](#execute)|實作這個方法與這個物件相關聯的控制代碼會變成收到信號時執行程式碼。|  
  
## <a name="remarks"></a>備註  
 當您需要以回應變得收到信號的控制代碼的工作者執行緒上執行的程式碼時，請實作這個介面。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle  
 實作這個方法關閉此控制代碼，這個物件相關聯。  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>參數  
 *hHandle*  
 若要關閉控制代碼。  
  
### <a name="return-value"></a>傳回值  
 在成功或失敗的錯誤 HRESULT 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼示範的簡單實作`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>  IWorkerThreadClient::Execute  
 實作這個方法與這個物件相關聯的控制代碼會變成收到信號時執行程式碼。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>參數  
 `dwParam`  
 User 參數。  
  
 `hObject`  
 被通知控制代碼。  
  
### <a name="return-value"></a>傳回值  
 在成功或失敗的錯誤 HRESULT 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼和 DWORD/指標傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼示範的簡單實作`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)
