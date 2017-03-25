---
title: "IThreadProxy 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 0a002dc4440b4784dee7f808a9e3be8dd4f89124
ms.lasthandoff: 03/17/2017

---
# <a name="ithreadproxy-structure"></a>IThreadProxy 結構
執行緒的抽象概念。 視您所建立之排程器的 `SchedulerType` 原則機碼而定，資源管理員會授與您支援一般 Win32 執行緒或可使用者模式排程 (UMS) 執行緒的執行緒 Proxy。 安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。  
  
## <a name="syntax"></a>語法  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ithreadproxy:: Getid](#getid)|執行緒 proxy 傳回的唯一識別碼。|  
|[Ithreadproxy::](#switchout)|解除基礎虛擬處理器根內容的關聯。|  
|[Ithreadproxy:: Switchto](#switchto)|執行從目前執行內容的合作式內容切換到另一個。|  
|[Ithreadproxy:: Yieldtosystem](#yieldtosystem)|造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選擇下一個要執行的執行緒。|  
  
## <a name="remarks"></a>備註  
 執行緒 proxy 會結合介面所表示的執行內容`IExecutionContext`分派工作的方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IThreadProxy`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="getid"></a>Ithreadproxy:: Getid 方法  
 執行緒 proxy 傳回的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 唯一整數識別碼。  
  
##  <a name="switchout"></a>Ithreadproxy:: 方法  
 解除基礎虛擬處理器根內容的關聯。  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>參數  
 `switchState`  
 表示執行緒 proxy 執行切換狀態。 參數的類型是`SwitchingProxyState`。  
  
### <a name="remarks"></a>備註  
 如果因故需要將內容與其執行所在的虛擬處理器根解除關聯，請使用 `SwitchOut`。 根據您傳遞給 `switchState` 參數的值，以及它是否在虛擬處理器根上執行而定，呼叫會立即傳回或是封鎖與內容相關聯的執行緒 Proxy。 在將參數設定為 `SwitchOut` 的情況下呼叫 `Idle` 是錯誤的做法。 這樣會導致[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。  
  
 無論是因為資源管理員的指示，或是您要求暫時過度訂閱虛擬處理器根，但已經不再需要這樣做，只要您想要減少排程器擁有的虛擬處理器根數目，`SwitchOut` 都會很有用。 在此情況下應該叫用方法[IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4)上的虛擬處理器根，然後再呼叫到`SwitchOut`參數`switchState`設為`Blocking`。 這樣將會封鎖執行緒 Proxy，而且它會在排程器中有不同的虛擬處理器根可用於執行時繼續執行。 呼叫函式可以繼續封鎖執行緒 proxy`SwitchTo`切換到這個執行緒 proxy 的執行內容。 您也可以繼續執行緒 proxy，若要啟用虛擬處理器根使用其關聯的內容。 如需有關如何執行這項操作的詳細資訊，請參閱[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 當您想要重新初始化虛擬處理器，讓它能夠在未來發生封鎖執行緒 Proxy，或是暫時將它卸離執行所在的虛擬處理器根以及對其分派工作的排程器時可以啟動，您也可以使用 `SwitchOut`。 如果您想要封鎖執行緒 Proxy，請使用 `SwitchOut`，並將 `switchState` 參數設定為 `Blocking`。 之後可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 讓它繼續執行，如上面所述。 當您想要暫時將這個執行緒 Proxy 卸離執行所在的虛擬處理器根，以及與虛擬處理器相關聯的排程器，請使用 `SwitchOut` 並將參數設定為 `Nesting`。 若呼叫 `SwitchOut` 並將 `switchState` 參數設定為 `Nesting` 時，它正在虛擬處理器根上執行，則會造成根重新初始化，而且目前執行緒 Proxy 會繼續執行，不需要根。 執行緒 proxy 會被視為已離開排程器，直到它會呼叫[ithreadproxy::](#switchout)方法`Blocking`在稍後的時間。 第二次呼叫 `SwitchOut` 並將參數設定為 `Blocking` 時，該呼叫會將內容返回已封鎖狀態，以便在卸離的排程器中透過 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 繼續執行。 由於它並未在虛擬處理器根上執行，因此不會發生重新初始化。  
  
 已重新初始化的虛擬處理器根與資源管理員授與排程器的全新虛擬處理器根並無不同。 您可以在執行內容中使用 `IVirtualProcessorRoot::Activate` 啟用它，這樣就可以用它來執行。  
  
 `SwitchOut`必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行的執行緒或結果。  
  
 在隨附於 Visual Studio 2010 的程式庫和標頭中，這個方法不會使用參數，也不會重新初始化虛擬處理器根。 若要保留舊有行為，可以提供預設參數值 `Blocking`。  
  
##  <a name="switchto"></a>Ithreadproxy:: Switchto 方法  
 執行從目前執行內容的合作式內容切換到另一個。  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 若要以合作方式切換至執行內容。  
  
 `switchState`  
 表示執行緒 proxy 執行切換狀態。 參數的類型是`SwitchingProxyState`。  
  
### <a name="remarks"></a>備註  
 使用這個方法從一個執行內容切換至另一個，從[iexecutioncontext:: Dispatch](iexecutioncontext-structure.md#dispatch)方法的第一個執行內容。 此方法將相關聯的執行內容`pContext`如果它尚未與其中一個相關聯的執行緒 proxy。 目前的執行緒 proxy 的擁有權由您指定的值`switchState`引數。  
  
 使用值`Idle`當您想要傳回至資源管理員目前正在執行的執行緒 proxy。 呼叫`SwitchTo`參數`switchState`設`Idle`會導致執行內容`pContext`啟動基礎執行資源上執行。 這個執行緒 proxy 的擁有權轉移給資源管理員，並想要傳回的執行內容`Dispatch`方法後立即`SwitchTo`傳回，才能完成轉送。 已分派執行緒 proxy 的執行內容會解除關聯的執行緒 proxy，並排程器可以自由地重複使用或任意損毀。  
  
 使用值`Blocking`當您想要這個執行緒 proxy 會進入封鎖的狀態。 呼叫`SwitchTo`參數`switchState`設`Blocking`會導致執行內容`pContext`開始執行，並封鎖目前執行緒 proxy，直到它繼續執行。 排程器執行緒 proxy 時，保留擁有權的執行緒 proxy`Blocking`狀態。 呼叫函式可以繼續封鎖執行緒 proxy`SwitchTo`切換到這個執行緒 proxy 的執行內容。 您也可以繼續執行緒 proxy，若要啟用虛擬處理器根使用其關聯的內容。 如需有關如何執行這項操作的詳細資訊，請參閱[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 使用值`Nesting`當您想要暫時這個執行緒 proxy 卸離執行所在的虛擬處理器根以及排程器，它會分派工作的。 呼叫`SwitchTo`參數`switchState`設`Nesting`會導致執行內容`pContext`啟動執行與目前執行緒 proxy 也會繼續執行而不需要虛擬處理器根。 執行緒 proxy 會被視為已離開排程器，直到它會呼叫[ithreadproxy::](#switchout)方法，在稍後的時間。 `IThreadProxy::SwitchOut`虛擬處理器根可用於重新排定它前方法無法封鎖執行緒 proxy。  
  
 `SwitchTo`必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行的執行緒或結果。 函式會擲回`invalid_argument`如果參數`pContext`設為`NULL`。  
  
##  <a name="yieldtosystem"></a>Ithreadproxy:: Yieldtosystem 方法  
 造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選擇下一個要執行的執行緒。  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>備註  
 一般的 Windows 執行緒，支援的執行緒 proxy 呼叫時`YieldToSystem`完全相同的 Windows 函式的行為`SwitchToThread`。 不過，當從使用者模式可排程 (UMS) 執行緒呼叫`SwitchToThread`函式委派挑選下一個要執行以使用者模式排程器，不是作業系統執行緒的工作。 若要達成的系統中切換至不同的就緒執行緒所需的效果，請使用`YieldToSystem`。  
  
 `YieldToSystem`必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行的執行緒或結果。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IExecutionContext 結構](iexecutioncontext-structure.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)

