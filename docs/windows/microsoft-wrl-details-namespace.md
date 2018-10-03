---
title: Microsoft::WRL::Details 命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f95eaa49db5e09bceaefafc16312250d823e5d5c
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250389"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details 命名空間

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[ComPtrRef 類別](../windows/comptrref-class.md)|表示 ComPtr 型別的物件的參考\<T >。|
|[ComPtrRefBase 類別](../windows/comptrrefbase-class.md)|表示基底類別[ComPtrRef](../windows/comptrref-class.md)類別。|
|[DontUseNewUseMake 類別](../windows/dontusenewusemake-class.md)|防止使用運算子**新**在`RuntimeClass`。 因此，您必須使用[讓函式](../windows/make-function.md)改。|
|[EventTargetArray 類別](../windows/eventtargetarray-class.md)|表示事件處理常式的陣列。|
|[MakeAllocator 類別](../windows/makeallocator-class.md)|配置記憶體可啟動類別，包含或不含弱式參考支援。|
|[ModuleBase 類別](../windows/modulebase-class.md)|表示基底類別[模組](../windows/module-class.md)類別。|
|[RemoveIUnknown 類別](../windows/removeiunknown-class.md)|建立類型，相當於`IUnknown`為基礎的類型，但有非虛擬`QueryInterface`， `AddRef`，和`Release`方法。|
|[WeakReference 類別](../windows/weakreference-class.md)|代表*弱式參考*可用於使用 Windows 執行階段或傳統 com 使用。 弱式參考代表不一定可存取的物件。|

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[ArgTraits 結構](../windows/argtraits-structure.md)|介面和匿名的成員函式具有指定的參數數目，請宣告指定的委派。|
|[ArgTraitsHelper 結構](../windows/argtraitshelper-structure.md)|可協助定義委派引數的一般的特性。|
|[BoolStruct 結構](../windows/boolstruct-structure.md)|定義是否`ComPtr`管理介面的物件存留期。 `BoolStruct` 會在內部使用[BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)運算子。|
|[CreatorMap 結構](../windows/creatormap-structure.md)|包含如何初始化、 註冊和取消註冊物件的相關資訊。|
|[DerefHelper 結構](../windows/derefhelper-structure.md)|代表已取值的指標，要`T*`樣板參數。|
|[EnableIf 結構](../windows/enableif-structure.md)|如果第一個範本參數評估為第二個範本參數所指定之型別的資料成員會定義 **，則為 true**。|
|[FactoryCache 結構](../windows/factorycache-structure.md)|包含的 class factory 和值，識別已註冊的 Windows 執行階段或 COM 類別物件的位置。|
|[ImplementsBase 結構](../windows/implementsbase-structure.md)|用來驗證範本中的參數型別[Implements 結構](../windows/implements-structure.md)。|
|[ImplementsHelper 結構](../windows/implementshelper-structure.md)|可協助實作[實作](../windows/implements-structure.md)結構。|
|[InterfaceList 結構](../windows/interfacelist-structure.md)|用來建立介面的遞迴清單。|
|[InterfaceListHelper 結構](../windows/interfacelisthelper-structure.md)|建置`InterfaceList`以遞迴方式套用指定的範本參數引數型別。|
|[InterfaceTraits 結構](../windows/interfacetraits-structure.md)|實作的介面的一般特性。|
|[InvokeHelper 結構](../windows/invokehelper-structure.md)|提供實作`Invoke()`方法根據指定的數目和類型的引數。|
|[IsBaseOfStrict 結構](../windows/isbaseofstrict-structure.md)|測試某個類型是否為另一個類型的基底。|
|[IsSame 結構](../windows/issame-structure.md)|其中一個指定的型別是否相當於另一個測試指定的類型。|
|[Nil 結構](../windows/nil-structure.md)|用來指出未指定，選用的範本參數。|
|[RemoveReference 結構](../windows/removereference-structure.md)|移除參考或右值參考特性，從指定的類別範本參數。|
|[RuntimeClassBase 結構](../windows/runtimeclassbase-structure.md)|用來偵測`RuntimeClass`中[讓](../windows/make-function.md)函式。|
|[RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)|提供 helper 方法來`QueryInterface`作業和取得的介面識別碼。|
|[VerifyInheritanceHelper 結構](../windows/verifyinheritancehelper-structure.md)|測試是否有一個介面衍生自另一個介面。|
|[VerifyInterfaceHelper 結構](../windows/verifyinterfacehelper-structure.md)|確認範本參數所指定的介面符合特定需求。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[AsyncStatusInternal 列舉](../windows/asyncstatusinternal-enumeration.md)|指定狀態的非同步作業的內部列舉型別之間的對應和`Windows::Foundation::AsyncStatus`列舉型別。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[ActivationFactoryCallback 函式](../windows/activationfactorycallback-function.md)|取得啟用 factory 做為指定的啟用識別碼。|
|[Move 函式](../windows/move-function.md)|將指定的引數從一個位置移到另一個。|
|[RaiseException 函式](../windows/raiseexception-function.md)|引發的例外狀況，在呼叫的執行緒。|
|[Swap 函式 (WRL)](../windows/swap-function-wrl.md)|交換兩個指定的引數的值。|
|[TerminateMap 函式](../windows/terminatemap-function.md)|關閉指定的模組中的 class factory。|

## <a name="requirements"></a>需求

**標頭：** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)