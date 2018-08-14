---
title: 索引鍵 WRL 應用程式開發介面的類別目錄 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9936c85443f893111b3c2b9de17ca80e6fb382b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881454"
---
# <a name="key-wrl-apis-by-category"></a>依分類區分的重要 WRL 應用程式開發介面
下表列出主 Windows 執行階段 c + + 樣板程式庫類別、 結構、 函數和巨集。 會省略 helper 命名空間和類別中的建構。 這些清單會擴大，命名空間所排列的 API 文件。  
  
### <a name="classes"></a>類別  
  
|標題|描述|  
|-----------|-----------------|  
|[ActivationFactory 類別](../windows/activationfactory-class.md)|讓 Windows 執行階段啟動一或多個類別。|  
|[AsyncBase 類別](../windows/asyncbase-class.md)|實作 Windows 執行階段非同步狀態機器。|  
|[ClassFactory 類別](../windows/classfactory-class.md)|實作 `IClassFactory` 介面的基本功能。|  
|[ComPtr 類別](../windows/comptr-class.md)|建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。|  
|[Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)|表示事件。|  
|[EventSource 類別](../windows/eventsource-class.md)|表示事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。|  
|[FtmBase 類別](../windows/ftmbase-class.md)|代表無限制執行緒封送處理器物件。|  
|[HandleT 類別](../windows/handlet-class.md)|物件，表示控制代碼。|  
|[HString 類別](../windows/hstring-class.md)|提供支援管理 HSTRING 控制代碼。|  
|[HStringReference 類別](../windows/hstringreference-class.md)|代表 HSTRING 建立從現有的字串。|  
|[Module 類別](../windows/module-class.md)|表示相關物件的集合。|  
|[Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。|  
|[Module::MethodReleaseNotifier 類別](../windows/module-methodreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-到-a-方法成員所指定的事件處理常式。|  
|[Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)|在模組中的最後一個物件發行時，會叫用事件處理常式。|  
|[RoInitializeWrapper 類別](../windows/roinitializewrapper-class.md)|初始化 Windows 執行階段。|  
|[RuntimeClass 類別](../windows/runtimeclass-class.md)|表示繼承指定數目的介面的具現化類別，並提供指定的 Windows 執行階段、傳統 COM 和弱式參考支援。|  
|[SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)|提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。|  
|[SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)|提供基本機制以建立基底類別。|  
|[WeakRef 類別](../windows/weakref-class.md)|代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。|  
  
### <a name="structures"></a>結構  
  
|標題|描述|  
|-----------|-----------------|  
|[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)|指定可以套用至一組介面 ID 的驗證和初始化函式。|  
|[CloakedIid 結構](../windows/cloakediid-structure.md)|表示要`RuntimeClass`，`Implements`和`ChainInterfaces`範本指定的介面不是在 IID 清單中存取。|  
|[Implements 結構](../windows/implements-structure.md)|實作`QueryInterface`和`GetIid`指定介面。|  
|[MixIn 結構](../windows/mixin-structure.md)|確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。|  
  
### <a name="functions"></a>函式  
  
|標題|描述|  
|-----------|-----------------|  
|[ActivateInstance 函式](../windows/activateinstance-function.md)|註冊並擷取在指定的類別識別碼中所定義之指定類型的執行個體|  
|[AsWeak 函式](../windows/asweak-function.md)|擷取指定執行個體的弱式參考。|  
|[回呼函式](../windows/callback-function-windows-runtime-cpp-template-library.md)|建立成員函式是回呼方法的物件。|  
|[CreateActivationFactory 函式](../windows/createactivationfactory-function.md)|建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。|  
|[CreateClassFactory 函式](../windows/createclassfactory-function.md)|建立會產生指定類別之執行個體的處理站。|  
|[GetActivationFactory 函式](../windows/getactivationfactory-function.md)|擷取的範本參數所指定之類型的啟動 factory。|  
|[Make 函式](../windows/make-function.md)|初始化指定的 Windows 執行階段類別。|  
  
### <a name="macros"></a>巨集  
  
|標題|描述|  
|-----------|-----------------|  
|[ActivatableClass 巨集](../windows/activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的 factory。|  
|[InspectableClass 巨集](../windows/inspectableclass-macro.md)|設定執行階段類別名稱和信任層級。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)