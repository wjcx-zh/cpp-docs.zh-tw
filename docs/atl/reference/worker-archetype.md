---
title: "背景工作原型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a408af2ac7de2f71c98467e08c49187c346304e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="worker-archetype"></a>背景工作原型
類別符合*工作者*原型提供程式碼以處理序的工作項目排入佇列的執行緒集區上。  
  
 **實作**  
  
 若要實作的類別符合這個原型，類別必須提供下列功能：  
  
|方法|說明|  
|------------|-----------------|  
|[初始化](#initialize)|呼叫以初始化背景工作物件傳遞至任何要求之前[Execute](#execute)。|  
|[執行](#execute)|呼叫以處理工作項目。|  
|[終止](#terminate)|停止背景工作物件初始化之後的所有要求已都傳遞至呼叫[Execute](#execute)。|  
  
|Typedef|說明|  
|-------------|-----------------|  
|[RequestType](#requesttype)|可處理的背景工作類別的工作項目類型的 typedef。|  
  
 一般*工作者*類別看起來像這樣：  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **現有的實作**  
  
 這些類別符合這個原型：  
  
|類別|說明|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|收到要求在執行緒集區，並將它們傳遞至背景工作物件，會建立並終結針對每個要求。|  
  
 **使用**  
  
 這些範本參數預期的類別，以符合此原型：  
  
|參數名稱|使用對象|  
|--------------------|-------------|  
|*背景工作*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*背景工作*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
呼叫以處理工作項目。  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>參數  
 `request`  
 處理工作項目。 工作項目屬於相同的型別`RequestType`。  
  
 `pvWorkerParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Initialize`和`Terminate`。  
  
 `pOverlapped`  
 指標[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)結構，用來建立的工作項目排入佇列的佇列。  
  
## <a name="initialize"></a>WorkerArchetype::Initialize
呼叫以初始化背景工作物件傳遞至任何要求之前`WorkerArchetype::Execute`。  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>參數  
 `pvParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="requesttype"></a>WorkerArchetype::RequestType
可處理的背景工作類別的工作項目類型的 typedef。  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>備註  
 這個類型必須做的第一個參數`WorkerArchetype::Execute`和必須能夠與 ULONG_PTR 轉型。  
  
## <a name="terminate"></a>WorkerArchetype::Terminate
停止背景工作物件初始化之後的所有要求已都傳遞至呼叫`WorkerArchetype::Execute`)。  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>參數  
 `pvParam`  
 了解的背景工作類別的自訂參數。 也會傳遞至`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。  
  
## <a name="see-also"></a>另請參閱  
 [Archetypes](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)



