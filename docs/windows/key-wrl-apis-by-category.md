---
title: "依分類區分的重要 WRL 應用程式開發介面 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 依分類區分的重要 WRL 應用程式開發介面
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表列出主要 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 類別、 結構、 函式和巨集。 略過在 helper 命名空間和類別的建構。 這些清單會增加命名空間所排列的 API 文件。  
  
### <a name="classes"></a>類別  
  
|標題|說明|  
|-----------|-----------------|  
|[ActivationFactory 類別](../windows/activationfactory-class.md)|讓 Windows 執行階段啟動一或多個類別。|  
|[AsyncBase 類別](../windows/asyncbase-class.md)|實作 Windows 執行階段非同步狀態機器。|  
|[ClassFactory 類別](../windows/classfactory-class.md)|實作 `IClassFactory` 介面的基本功能。|  
|[ComPtr 類別](../windows/comptr-class.md)|建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。|  
|[事件類別 （Windows 執行階段 c + + 樣板程式庫）](../windows/event-class-windows-runtime-cpp-template-library.md)|表示事件。|  
|[EventSource 類別](../windows/eventsource-class.md)|表示事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。|  
|[FtmBase 類別](../windows/ftmbase-class.md)|代表無限制執行緒封送處理器物件。|  
|[HandleT 類別](../windows/handlet-class.md)|表示控制代碼的物件。|  
|[HString 類別](../windows/hstring-class.md)|提供支援操作 HSTRING 控點。|  
|[HStringReference 類別](../windows/hstringreference-class.md)|代表 HSTRING 建立從現有的字串。|  
|[模組類別](../windows/module-class.md)|表示相關物件的集合。|  
|[Genericreleasenotifier 類別](../windows/module-genericreleasenotifier-class.md)|發行目前模組中的最後一個物件時，會叫用事件處理常式。 事件處理常式是 lambda、 仿函式或函式指標上所指定的。|  
|[Methodreleasenotifier 類別](../windows/module-methodreleasenotifier-class.md)|發行目前模組中的最後一個物件時，會叫用事件處理常式。 事件處理常式是由物件和指定其指標-至-a-方法的成員。|  
|[Releasenotifier 類別](../windows/module-releasenotifier-class.md)|發行在模組中的最後一個物件時，會叫用事件處理常式。|  
|[RoInitializeWrapper 類別](../windows/roinitializewrapper-class.md)|初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。|  
|[RuntimeClass 類別](../windows/runtimeclass-class.md)|表示繼承指定數目的介面的具現化類別，並提供指定的 Windows 執行階段、傳統 COM 和弱式參考支援。|  
|[SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)|提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。|  
|[SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)|提供基本機制以建立基底類別。|  
|[WeakRef 類別](../windows/weakref-class.md)|代表 *弱式參考* ，可以由只有 Windows 執行階段，不是傳統 com 使用。 弱式參考代表不一定可存取的物件。|  
  
### <a name="structures"></a>結構  
  
|標題|說明|  
|-----------|-----------------|  
|[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)|指定可以套用至一組介面 ID 的驗證和初始化函式。|  
|[CloakedIid 結構](../windows/cloakediid-structure.md)|表示要 `RuntimeClass`, ，`Implements` 和 `ChainInterfaces` 範本指定的介面不是可存取 IID 清單中。|  
|[Implements 結構](../windows/implements-structure.md)|實作 `QueryInterface` 和 `GetIid` 指定的介面。|  
|[MixIn 結構](../windows/mixin-structure.md)|確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。|  
  
### <a name="functions"></a>函式  
  
|標題|說明|  
|-----------|-----------------|  
|[ActivateInstance 函式](../windows/activateinstance-function.md)|註冊並擷取執行個體指定的型別定義中指定的類別識別碼。|  
|[AsWeak 函式](../windows/asweak-function.md)|擷取指定執行個體的弱式參考。|  
|[回呼函式](../windows/callback-function-windows-runtime-cpp-template-library.md)|建立成員函式是回呼方法的物件。|  
|[CreateActivationFactory 函式](../windows/createactivationfactory-function.md)|建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。|  
|[CreateClassFactory 函式](../windows/createclassfactory-function.md)|建立會產生指定類別之執行個體的處理站。|  
|[GetActivationFactory 函式](../windows/getactivationfactory-function.md)|擷取類型範本參數所指定的啟用 factory。|  
|[Make 函式](../windows/make-function.md)|初始化指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別。|  
  
### <a name="macros"></a>巨集  
  
|標題|說明|  
|-----------|-----------------|  
|[ActivatableClass 巨集](../windows/activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的 factory。|  
|[InspectableClass 巨集](../windows/inspectableclass-macro.md)|設定執行階段類別名稱和信任層級。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)