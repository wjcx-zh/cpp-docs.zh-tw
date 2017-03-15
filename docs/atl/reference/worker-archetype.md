---
title: "背景工作原型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
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
ms.openlocfilehash: 046160644cca3bd23e4293a3c52692d2b4c94cd5
ms.lasthandoff: 02/24/2017

---
# <a name="worker-archetype"></a>背景工作原型
符合類別*工作者*原型中提供的程式碼程序的工作項目佇列排入執行緒集區。  
  
 **實作**  
  
 若要實作符合此原型的類別，類別必須提供下列功能︰  
  
|方法|說明|  
|------------|-----------------|  
|[初始化](#initialize)|呼叫以初始化背景工作物件之前的任何要求轉寄給[Execute](#execute)。|  
|[執行](#execute)|呼叫來處理工作項目。|  
|[終止](#terminate)|停止背景工作物件初始化之後的所有要求已都傳遞至呼叫[Execute](#execute)。|  
  
|Typedef|說明|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Typedef，可處理的背景工作類別的工作項目類型。|  
  
 一般*工作者*類別看起來像這樣︰  
  
 [!code-cpp[NVC_ATL_Utilities #&137;](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **現有的實作**  
  
 這些類別符合這個原型︰  
  
|類別|描述|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|從執行緒集區接收要求，並將它們傳遞到背景工作物件的建立和摧毀針對每個要求。|  
  
 **使用**  
  
 這些範本參數預期的類別，以符合此原型︰  
  
|參數名稱|使用對象|  
|--------------------|-------------|  
|*背景工作*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*背景工作*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
## <a name="a-nameexecuteaworkerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Execute
呼叫來處理工作項目。  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>參數  
 `request`  
 處理工作項目。 工作項目是相同型別的`RequestType`。  
  
 `pvWorkerParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Initialize`和`Terminate`。  
  
 `pOverlapped`  
 指標[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)結構，用來建立的工作項目排入佇列的佇列。  
  
## <a name="a-nameinitializea-workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialize
呼叫以初始化背景工作物件之前的任何要求轉寄給`WorkerArchetype::Execute`。  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>參數  
 `pvParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="a-namerequesttypea-workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType
Typedef，可處理的背景工作類別的工作項目類型。  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>備註  
 此類型必須做的第一個參數`WorkerArchetype::Execute`和必須能夠從 ULONG_PTR 來回轉換。  
  
## <a name="a-nameterminatea-workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Terminate
停止背景工作物件初始化之後的所有要求已都傳遞至呼叫`WorkerArchetype::Execute`)。  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>參數  
 `pvParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。  
  
## <a name="see-also"></a>另請參閱  
 [Archetype](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)




