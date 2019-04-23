---
title: 依分類區分的重要 WRL 應用程式開發介面
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: f3065323c567c944dab12fc1ebbcbd6bb57127e9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039049"
---
# <a name="key-wrl-apis-by-category"></a>依分類區分的重要 WRL 應用程式開發介面

下表列出主要的 Windows 執行階段C++樣板程式庫類別、 結構、 函式和巨集。 協助程式的命名空間和類別的建構會省略。 這些清單會增加命名空間所排列的 API 文件。

## <a name="classes"></a>類別

|標題|描述|
|-----------|-----------------|
|[ActivationFactory 類別](activationfactory-class.md)|讓 Windows 執行階段啟動一或多個類別。|
|[AsyncBase 類別](asyncbase-class.md)|實作 Windows 執行階段非同步狀態機器。|
|[ClassFactory 類別](classfactory-class.md)|實作 `IClassFactory` 介面的基本功能。|
|[ComPtr 類別](comptr-class.md)|建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。|
|[Event 類別 (Windows 執行階段 C++ 範本庫)](event-class-wrl.md)|表示事件。|
|[EventSource 類別](eventsource-class.md)|表示事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。|
|[FtmBase 類別](ftmbase-class.md)|代表無限制執行緒封送處理器物件。|
|[HandleT 類別](handlet-class.md)|物件表示的控制代碼。|
|[HString 類別](hstring-class.md)|提供對管理 HSTRING 控制代碼支援。|
|[HStringReference 類別](hstringreference-class.md)|表示從現有字串建立的 HSTRING。|
|[Module 類別](module-class.md)|表示相關物件的集合。|
|[Module::GenericReleaseNotifier 類別](module-genericreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。|
|[Module::MethodReleaseNotifier 類別](module-methodreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-至-a-方法成員所指定的事件處理常式。|
|[Module::ReleaseNotifier 類別](module-releasenotifier-class.md)|發行模組中的最後一個物件時，會叫用事件處理常式。|
|[RoInitializeWrapper 類別](roinitializewrapper-class.md)|初始化 Windows 執行階段。|
|[RuntimeClass 類別](runtimeclass-class.md)|表示繼承指定數目的介面的具現化類別，並提供指定的 Windows 執行階段、傳統 COM 和弱式參考支援。|
|[SimpleActivationFactory 類別](simpleactivationfactory-class.md)|提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。|
|[SimpleClassFactory 類別](simpleclassfactory-class.md)|提供基本機制以建立基底類別。|
|[WeakRef 類別](weakref-class.md)|代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。|

## <a name="structures"></a>結構

|標題|描述|
|-----------|-----------------|
|[ChainInterfaces 結構](chaininterfaces-structure.md)|指定可以套用至一組介面 ID 的驗證和初始化函式。|
|[CloakedIid 結構](cloakediid-structure.md)|若要指出`RuntimeClass`，`Implements`和`ChainInterfaces`範本指定的介面不是在 IID 清單中存取。|
|[Implements 結構](implements-structure.md)|Implements`QueryInterface`和`GetIid`指定介面。|
|[MixIn 結構](mixin-structure.md)|確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。|

## <a name="functions"></a>函式

|標題|描述|
|-----------|-----------------|
|[ActivateInstance 函式](activateinstance-function.md)|註冊，並擷取在指定的類別識別碼所定義之指定類型的執行個體|
|[AsWeak 函式](asweak-function.md)|擷取指定執行個體的弱式參考。|
|[回呼函式](callback-function-wrl.md)|建立成員函式是回呼方法的物件。|
|[CreateActivationFactory 函式](createactivationfactory-function.md)|建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。|
|[CreateClassFactory 函式](createclassfactory-function.md)|建立會產生指定類別之執行個體的處理站。|
|[GetActivationFactory 函式](getactivationfactory-function.md)|擷取的範本參數所指定之類型的啟用 factory。|
|[Make 函式](make-function.md)|初始化指定的 Windows 執行階段類別。|

## <a name="macros"></a>巨集

|標題|描述|
|-----------|-----------------|
|[ActivatableClass 巨集](activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。|
|[InspectableClass 巨集](inspectableclass-macro.md)|設定執行階段類別名稱和信任層級。|

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)