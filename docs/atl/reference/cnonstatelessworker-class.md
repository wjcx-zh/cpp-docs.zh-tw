---
title: "CNonStatelessWorker 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs: C++
helpviewer_keywords: CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08b440a60b23182c3efff1c0236773ad2b98bf97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 類別
從執行緒集區接收要求，並將它們傳遞到會建立並終結背景工作物件中，每個要求。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>參數  
 *背景工作*  
 背景工作執行緒類別符合[工作者原型](../../atl/reference/worker-archetype.md)適合處理要求佇列上[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|實作[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|實作[WorkerArchetype::Execute](worker-archetype.md#execute)。|  
|[CNonStatelessWorker::Initialize](#initialize)|實作[WorkerArchetype::Initialize](worker-archetype.md#initialize)。|  
|[CNonStatelessWorker::Terminate](#terminate)|實作[WorkerArchetype::Terminate](worker-archetype.md#terminate)。|  
  
## <a name="remarks"></a>備註  
 這個類別是用於簡單的工作者執行緒[CThreadPool](../../atl/reference/cthreadpool-class.md)。 這個類別不會提供自己的任何要求處理功能。 相反地，它會具現化一個執行個體*工作者*每個要求並委派至該執行個體，其方法的實作。  
  
 這個類別的好處是，它會提供便利的方式來變更現有的背景工作執行緒類別的狀態模型。 `CThreadPool`將建立的單一工作者執行緒的存留期間，如果背景工作類別保存狀態，它會保留它在多個要求。 藉由只包裝在該類別`CNonStatelessWorker`範本，然後再將它與`CThreadPool`、 存留期，背景工作以及它所保留限制為單一要求的狀態。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
##  <a name="execute"></a>CNonStatelessWorker::Execute  
 實作[WorkerArchetype::Execute](worker-archetype.md#execute)。  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>備註  
 這個方法建立的執行個體*工作者*類別上的堆疊和呼叫[初始化](worker-archetype.md#initialize)上該物件。 如果初始化成功，這個方法也會呼叫[Execute](worker-archetype.md#execute)和[Terminate](worker-archetype.md#terminate)相同物件上。  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 實作[WorkerArchetype::Initialize](worker-archetype.md#initialize)。  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 這個類別不會執行任何初始設定`Initialize`。  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 實作[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>備註  
 這個類別會處理相同類型的工作項目為類別，用於*工作者*樣板參數。 請參閱[CNonStatelessWorker 概觀](../../atl/reference/cnonstatelessworker-class.md)如需詳細資訊。  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 實作[WorkerArchetype::Terminate](worker-archetype.md#terminate)。  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>備註  
 這個類別不會執行任何清理`Terminate`。  
  
## <a name="see-also"></a>另請參閱  
 [CThreadPool 類別](../../atl/reference/cthreadpool-class.md)   
 [背景工作原型](../../atl/reference/worker-archetype.md)   
 [類別](../../atl/reference/atl-classes.md)
