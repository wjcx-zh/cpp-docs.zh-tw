---
title: "IVirtualProcessorRoot 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
dev_langs: C++
helpviewer_keywords: IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1010517799b9878ff88ddbc68a76ff4a0ed6588f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構
執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ivirtualprocessorroot:: Activate](#activate)|會導致執行內容介面相關聯的執行緒 proxy`pContext`啟動這個虛擬處理器根上執行。|  
|[Ivirtualprocessorroot:: Deactivate](#deactivate)|造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行的呼叫上`Activate`方法。|  
|[Ivirtualprocessorroot:: Ensurealltasksvisible](#ensurealltasksvisible)|會儲存在個別處理器的記憶體階層，就會顯示在系統上的所有處理器的資料。 它可確保，完整記憶體範圍已執行的所有處理器方法傳回之前。|  
|[Ivirtualprocessorroot:: Getid](#getid)|傳回的虛擬處理器根的唯一識別碼。|  
  
## <a name="remarks"></a>備註  
 每個虛擬處理器根網站具有相關聯的執行資源。 `IVirtualProcessorRoot`介面繼承自[IExecutionResource](iexecutionresource-structure.md)介面。 多個虛擬處理器根可對應到相同的基礎硬體執行緒。  
  
 資源管理員可授與虛擬處理器根排程器，以回應要求的資源。 排程器可以使用虛擬處理器根，藉由啟用的執行內容中執行的工作。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="activate"></a>Ivirtualprocessorroot:: Activate 方法  
 會導致執行內容介面相關聯的執行緒 proxy`pContext`啟動這個虛擬處理器根上執行。  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 要將此虛擬處理器根分派的執行內容的介面。  
  
### <a name="remarks"></a>備註  
 資源管理員會提供執行緒 proxy，如果沒有相關聯的執行內容的介面`pContext`  
  
 `Activate`方法可以用來開始傳回資源管理員，在新虛擬處理器根上執行工作，或繼續執行緒上的 proxy 已停用訂閱或即將停用的虛擬處理器根。 請參閱[ivirtualprocessorroot:: Deactivate](#deactivate)如需有關停用。 當您正在繼續已停用的虛擬處理器根，參數`pContext`必須是用來停用的虛擬處理器根參數相同。  
  
 一旦虛擬處理器根啟動第一次呼叫後續組`Deactivate`和`Activate`可能會彼此競爭。 這表示它是可接受的資源管理員來接收呼叫`Activate`收到之前`Deactivate`已供的呼叫。  
  
 當您啟用虛擬處理器根時，您訊號至資源管理員，此虛擬處理器根工作與目前忙碌中。 如果您的排程器找不到要執行這個根目錄上的任何工作，它必須為叫用`Deactivate`告知資源管理員的虛擬處理器根處於閒置狀態的方法。 資源管理員會使用此資料進行負載平衡系統。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果擲回引數`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
 啟用虛擬處理器根中的動作會增加 1 基礎硬體執行緒的訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="deactivate"></a>Ivirtualprocessorroot:: Deactivate 方法  
 造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行的呼叫上`Activate`方法。  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 目前由這個根發送內容。  
  
### <a name="return-value"></a>傳回值  
 布林值。 值為`true`表示執行緒 proxy 傳回`Deactivate`方法以回應呼叫`Activate`方法。 值為`false`表示執行緒 proxy 傳回的資源管理員中的通知事件的回應中的方法。 使用者模式可排程 (UMS) 執行緒排程器上，這表示項目出現在排程器的完成清單中，而排程器，才能處理它們。  
  
### <a name="remarks"></a>備註  
 若要暫時停止執行的虛擬處理器根排程器中找不到任何工作時使用這個方法。 呼叫`Deactivate`方法必須源自內`Dispatch`執行內容的虛擬處理器根與上次啟動的方法。 換句話說，叫用執行緒 proxy`Deactivate`方法必須是目前正在執行的虛擬處理器根的一個。 未執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。  
  
 已停用的虛擬處理器根可能喚醒呼叫`Activate`方法，並有相同的引數中傳遞給`Deactivate`方法。 排程器會負責確保會呼叫`Activate`和`Deactivate`方法成對的但是這些不需要以特定順序接收。 資源管理員能夠接收呼叫`Activate`方法才收到呼叫`Deactivate`它所用的方法。  
  
 如果虛擬處理器根會喚醒並傳回值`Deactivate`方法就是值`false`，排程器應查詢 UMS 完成清單透過`IUMSCompletionList::GetUnblockNotifications`方法，該資訊之後，並接著呼叫`Deactivate`方法一次。 這應該重複直到為止`Deactivate`方法會傳回值`true`。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果從未啟用的虛擬處理器根，會擲回引數或`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
 中的停用虛擬處理器根動作減一的基礎硬體執行緒的訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="ensurealltasksvisible"></a>Ivirtualprocessorroot:: Ensurealltasksvisible 方法  
 會儲存在個別處理器的記憶體階層，就會顯示在系統上的所有處理器的資料。 它可確保，完整記憶體範圍已執行的所有處理器方法傳回之前。  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 這目前由發送這個虛擬處理器根內容。  
  
### <a name="remarks"></a>備註  
 當您想要加上新的工作依排程器的同步處理停用的虛擬處理器根作業，您會發現此方法很有用。 基於效能考量，您可以決定工作項目加入您的排程器不會執行記憶體屏障，這表示一個處理器上執行的執行緒所加入的工作項目不會立即顯示所有其他處理器。 使用此方法搭配`Deactivate`方法可確保您的排程器未停用所有虛擬處理器根工作項目存在於您的排程器的集合。  
  
 呼叫`EnsureAllTasksVisibleThe`方法必須源自內`Dispatch`執行內容的虛擬處理器根與上次啟動的方法。 換句話說，叫用執行緒 proxy`EnsureAllTasksVisible`方法必須是目前正在執行的虛擬處理器根的一個。 未執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果從未啟用的虛擬處理器根，會擲回引數或`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
##  <a name="getid"></a>Ivirtualprocessorroot:: Getid 方法  
 傳回的虛擬處理器根的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 整數識別碼。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
