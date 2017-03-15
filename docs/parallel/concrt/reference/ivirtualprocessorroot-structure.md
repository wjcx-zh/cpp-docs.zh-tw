---
title: "IVirtualProcessorRoot 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IVirtualProcessorRoot
dev_langs:
- C++
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 18
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: ca095a249ee0eb9e1393e232ab7957a7060a2002
ms.lasthandoff: 02/24/2017

---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構
執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ivirtualprocessorroot:: Activate 方法](#activate)|執行內容介面相關聯的執行緒 proxy 會導致`pContext`以啟動此虛擬處理器根上執行。|  
|[Ivirtualprocessorroot:: Deactivate 方法](#deactivate)|造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行的呼叫上`Activate`方法。|  
|[Ivirtualprocessorroot:: Ensurealltasksvisible 方法](#ensurealltasksvisible)|會造成記憶體階層中的個別處理器才會顯示所有處理器在系統上儲存的資料。 它可確保完整的記憶體範圍已經執行的所有處理器上的方法傳回之前。|  
|[Ivirtualprocessorroot:: Getid 方法](#getid)|傳回虛擬處理器根的唯一識別碼。|  
  
## <a name="remarks"></a>備註  
 每個虛擬處理器根有相關聯的執行資源。 `IVirtualProcessorRoot`介面繼承自[IExecutionResource](iexecutionresource-structure.md)介面。 多個虛擬處理器根可以對應到相同的基礎硬體執行緒。  
  
 資源管理員授與資源的要求回應中的排程器的虛擬處理器根。 排程器可以使用虛擬處理器根，來啟用它，這樣的執行內容中執行的工作。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-nameactivatea--ivirtualprocessorrootactivate-method"></a><a name="activate"></a>Ivirtualprocessorroot:: Activate 方法  
 執行內容介面相關聯的執行緒 proxy 會導致`pContext`以啟動此虛擬處理器根上執行。  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 要將此虛擬處理器根發送的執行內容的介面。  
  
### <a name="remarks"></a>備註  
 資源管理員會提供執行緒 proxy，如果沒有相關聯的執行內容的介面`pContext`  
  
 `Activate`開始傳回資源管理員，新的虛擬處理器根上執行工作，或繼續執行緒上的 proxy 已停用或即將停用的虛擬處理器根，可以使用方法。 請參閱[ivirtualprocessorroot:: Deactivate](#deactivate)如需有關停用。 當您正在繼續已停用的虛擬處理器根，參數`pContext`必須用來停用的虛擬處理器根參數相同。  
  
 一旦虛擬處理器根啟動第一次呼叫後續組`Deactivate`和`Activate`可能彼此競爭。 這表示它是可接受的資源管理員接收呼叫`Activate`之前收到`Deactivate`旨在的呼叫。  
  
 當您啟用虛擬處理器根時，您發出信號至資源管理員中此虛擬處理器根是正忙於進行工作。 如果您的排程器找不到任何在此根目錄上執行的工作，它應該叫用`Deactivate`告知資源管理員的虛擬處理器根閒置的方法。 資源管理員會使用此資料來進行負載平衡系統。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果擲回引數`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
 啟動虛擬處理器根的動作都會增加一個基礎硬體執行緒的訂閱層級。 如需有關訂閱層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="a-namedeactivatea--ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>Ivirtualprocessorroot:: Deactivate 方法  
 造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行的呼叫上`Activate`方法。  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 目前由這個根發送內容。  
  
### <a name="return-value"></a>傳回值  
 布林值。 值為`true`表示執行緒 proxy 傳回`Deactivate`方法以回應呼叫`Activate`方法。 值為`false`表示執行緒 proxy 傳回的資源管理員中的通知事件的回應中的方法。 使用者模式可排程 (UMS) 執行緒排程器上，這表示在排程器的完成清單會出現項目，且排程器需要處理它們。  
  
### <a name="remarks"></a>備註  
 若要暫時停止執行虛擬處理器根，當您找不到任何工作排程器中使用這個方法。 呼叫`Deactivate`方法必須源自內`Dispatch`執行內容的虛擬處理器根與上次啟動的方法。 換句話說，叫用執行緒 proxy`Deactivate`方法必須是一個虛擬處理器根上目前正在執行。 您並未在執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。  
  
 已停用的虛擬處理器根可能喚醒呼叫`Activate`方法，並有相同的引數，傳遞給`Deactivate`方法。 排程器會負責確保會呼叫`Activate`和`Deactivate`方法成對的但並不需要以特定順序接收。 資源管理員可以處理收到的呼叫`Activate`方法之前收到的呼叫`Deactivate`旨在的方法。  
  
 如果虛擬處理器根會喚醒並從傳回的值`Deactivate`方法就是值`false`，排程器應該查詢 UMS 完成清單，透過`IUMSCompletionList::GetUnblockNotifications`方法，此資訊，並接著呼叫`Deactivate`方法一次。 這應該重複做這類為止`Deactivate`方法會傳回值`true`。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果從未啟用的虛擬處理器根，會擲回或引數`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
 停用虛擬處理器根動作減一的基礎硬體執行緒的訂閱層級。 如需有關訂閱層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="a-nameensurealltasksvisiblea--ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>Ivirtualprocessorroot:: Ensurealltasksvisible 方法  
 會造成記憶體階層中的個別處理器才會顯示所有處理器在系統上儲存的資料。 它可確保完整的記憶體範圍已經執行的所有處理器上的方法傳回之前。  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 這目前由發送這個虛擬處理器根內容。  
  
### <a name="remarks"></a>備註  
 當您想要加上新的工作排程器的同步處理停用的虛擬處理器根，您會發現此方法很有用。 基於效能考量，您可能會決定新增至您的排程器的工作項目，而不執行記憶體屏障，這表示一個處理器上執行的執行緒所加入的工作項目不會立即顯示所有其他處理器。 使用此方法搭配`Deactivate`方法可確保您的排程器不會停用所有虛擬處理器根時的工作項目存在於您的排程器的集合。  
  
 呼叫`EnsureAllTasksVisibleThe`方法必須源自內`Dispatch`執行內容的虛擬處理器根與上次啟動的方法。 換句話說，叫用執行緒 proxy`EnsureAllTasksVisible`方法必須是一個虛擬處理器根上目前正在執行。 您並未在執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。  
  
 `invalid_argument`如果擲回引數`pContext`值`NULL`。  
  
 `invalid_operation`如果從未啟用的虛擬處理器根，會擲回或引數`pContext`不是由這個虛擬處理器根最近發送的執行內容。  
  
##  <a name="a-namegetida--ivirtualprocessorrootgetid-method"></a><a name="getid"></a>Ivirtualprocessorroot:: Getid 方法  
 傳回虛擬處理器根的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 整數識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

