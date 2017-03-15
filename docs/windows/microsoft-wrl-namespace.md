---
title: "Microsoft::WRL 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL"
  - "module/Microsoft::WRL"
  - "async/Microsoft::WRL"
  - "internal/Microsoft::WRL"
  - "event/Microsoft::WRL"
  - "ftm/Microsoft::WRL"
  - "client/Microsoft::WRL"
  - "corewrappers/Microsoft::WRL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WRL 命名空間"
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft::WRL 命名空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義組成 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的基本類型。  
  
## <a name="syntax"></a>語法  
  
```  
namespace Microsoft::WRL;  
```  
  
## <a name="members"></a>Members  
  
### <a name="typedefs"></a>Typedef  
  
|名稱|描述|  
|----------|-----------------|  
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[ActivationFactory 類別](../windows/activationfactory-class.md)|讓 Windows 執行階段啟動一或多個類別。|  
|[AsyncBase 類別](../windows/asyncbase-class.md)|實作 Windows 執行階段非同步狀態機器。|  
|[ClassFactory 類別](../windows/classfactory-class.md)|實作 `IClassFactory` 介面的基本功能。|  
|[ComPtr 類別](../windows/comptr-class.md)|建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。|  
|[DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)|範本類別，用於延期的事件引數類型。|  
|[EventSource 類別](../windows/eventsource-class.md)|表示事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。|  
|[FtmBase 類別](../windows/ftmbase-class.md)|代表無限制執行緒封送處理器物件。|  
|[模組類別](../windows/module-class.md)|表示相關物件的集合。|  
|[RuntimeClass 類別](../windows/runtimeclass-class.md)|表示繼承指定數目的介面的具現化類別，並提供指定的 Windows 執行階段、傳統 COM 和弱式參考支援。|  
|[SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)|提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。|  
|[SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)|提供基本機制以建立基底類別。|  
|[WeakRef 類別](../windows/weakref-class.md)|代表 *弱式參考* ，可以由只有 Windows 執行階段，不是傳統 com 使用。 弱式參考代表不一定可存取的物件。|  
  
### <a name="structures"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)|指定可以套用至一組介面 ID 的驗證和初始化函式。|  
|[CloakedIid 結構](../windows/cloakediid-structure.md)|指出 RuntimeClass、Implements 和 ChainInterfaces 範本指定介面無法在 IID 清單中存取。|  
|[Implements 結構](../windows/implements-structure.md)|實作指定介面的 QueryInterface 和 GetIid。|  
|[MixIn 結構](../windows/mixin-structure.md)|確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。|  
|[RuntimeClassFlags 結構](../windows/runtimeclassflags-structure.md)|包含的執行個體的型別 [RuntimeClass](../windows/runtimeclass-class.md)。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|說明|  
|----------|-----------------|  
|[AsyncResultType 列舉](../windows/asyncresulttype-enumeration.md)|指定 GetResults() 方法所傳回的結果類型。|  
|[ModuleType 列舉](../windows/moduletype-enumeration.md)|指定模組是否應支援同處理序伺服程式或跨處理序伺服程式。|  
|[RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)|指定的型別 [RuntimeClass](../windows/runtimeclass-class.md) 支援執行個體。|  
  
### <a name="functions"></a>函式  
  
|名稱|說明|  
|----------|-----------------|  
|[AsWeak 函式](../windows/asweak-function.md)|擷取指定執行個體的弱式參考。|  
|[回呼函式](../windows/callback-function-windows-runtime-cpp-template-library.md)|建立成員函式是回呼方法的物件。|  
|[CreateActivationFactory 函式](../windows/createactivationfactory-function.md)|建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。|  
|[CreateClassFactory 函式](../windows/createclassfactory-function.md)|建立會產生指定類別之執行個體的處理站。|  
|[Make 函式](../windows/make-function.md)|初始化指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)