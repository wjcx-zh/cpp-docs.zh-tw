---
title: Microsoft::WRL 命名空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: c92251dacbfa17e8f1ac0cbdc41aa9b06118ac91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213768"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL 命名空間

定義組成 Windows 執行階段C++範本庫的基本類型。

## <a name="syntax"></a>語法

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[ActivationFactory 類別](activationfactory-class.md)|讓 Windows 執行階段啟動一或多個類別。|
|[AsyncBase 類別](asyncbase-class.md)|實作 Windows 執行階段非同步狀態機器。|
|[ClassFactory 類別](classfactory-class.md)|實作 `IClassFactory` 介面的基本功能。|
|[ComPtr 類別](comptr-class.md)|建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。|
|[DeferrableEventArgs 類別](deferrableeventargs-class.md)|樣板類別，用於延遲的事件引數類型。|
|[EventSource 類別](eventsource-class.md)|表示事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。|
|[FtmBase 類別](ftmbase-class.md)|代表無限制執行緒封送處理器物件。|
|[Module 類別](module-class.md)|表示相關物件的集合。|
|[RuntimeClass 類別](runtimeclass-class.md)|表示繼承指定數目的介面的具現化類別，並提供指定的 Windows 執行階段、傳統 COM 和弱式參考支援。|
|[SimpleActivationFactory 類別](simpleactivationfactory-class.md)|提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。|
|[SimpleClassFactory 類別](simpleclassfactory-class.md)|提供基本機制以建立基底類別。|
|[WeakRef 類別](weakref-class.md)|代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。|

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[ChainInterfaces 結構](chaininterfaces-structure.md)|指定可以套用至一組介面 ID 的驗證和初始化函式。|
|[CloakedIid 結構](cloakediid-structure.md)|指出在 IID 清單中無法存取指定介面的 `RuntimeClass`、`Implements` 和 `ChainInterfaces` 範本。|
|[Implements 結構](implements-structure.md)|針對指定的介面，執行 `QueryInterface` 和 `GetIid`。|
|[MixIn 結構](mixin-structure.md)|確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。|
|[RuntimeClassFlags 結構](runtimeclassflags-structure.md)|包含[RuntimeClass](runtimeclass-class.md)實例的類型。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[AsyncResultType 列舉](asyncresulttype-enumeration.md)|指定 `GetResults()` 方法所傳回的結果類型。|
|[ModuleType 列舉](moduletype-enumeration.md)|指定模組是否應支援同處理序伺服程式或跨處理序伺服程式。|
|[RuntimeClassType 列舉](runtimeclasstype-enumeration.md)|指定支援的[RuntimeClass](runtimeclass-class.md)實例類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|----------|-----------------|
|[AsWeak 函式](asweak-function.md)|擷取指定執行個體的弱式參考。|
|[回呼函式 (WRL)](callback-function-wrl.md)|建立成員函式是回呼方法的物件。|
|[CreateActivationFactory 函式](createactivationfactory-function.md)|建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。|
|[CreateClassFactory 函式](createclassfactory-function.md)|建立會產生指定類別之執行個體的處理站。|
|[Make 函式](make-function.md)|初始化指定的 Windows 執行階段類別。|

## <a name="requirements"></a>需求

**標頭：** async .h、corewrappers、ftm、event .h、、implements、internal、module. h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](microsoft-wrl-wrappers-namespace.md)
