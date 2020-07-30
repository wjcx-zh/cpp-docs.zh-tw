---
title: Microsoft::WRL::Details 命名空間
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 50208242d77d7b54951bcb44608f1a20b5147efc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223469"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details 命名空間

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|說明|
|----------|-----------------|
|[ComPtrRef 類別](comptrref-class.md)|表示 ComPtr 類型之物件的參考 \<T> 。|
|[ComPtrRefBase 類別](comptrrefbase-class.md)|表示[ComPtrRef](comptrref-class.md)類別的基類。|
|[DontUseNewUseMake 類別](dontusenewusemake-class.md)|防止 `new` 在中使用運算子 `RuntimeClass` 。 因此，您必須改用[Make 函數](make-function.md)。|
|[EventTargetArray 類別](eventtargetarray-class.md)|表示事件處理常式的陣列。|
|[MakeAllocator 類別](makeallocator-class.md)|配置可啟動類別的記憶體，包含或不含弱式參考支援。|
|[ModuleBase 類別](modulebase-class.md)|表示[模組](module-class.md)類別的基類。|
|[RemoveIUnknown 類別](removeiunknown-class.md)|使類型等同于 `IUnknown` 型別，但具有非虛擬 `QueryInterface` 、 `AddRef` 和 `Release` 方法。|
|[WeakReference 類別](weakreference-class.md)|表示可以搭配 Windows 執行階段或傳統 COM 使用的*弱式參考*。 弱式參考代表不一定可存取的物件。|

### <a name="structures"></a>結構

|名稱|說明|
|----------|-----------------|
|[ArgTraits 結構](argtraits-structure.md)|宣告指定的委派介面，以及具有指定之參數數目的匿名成員函式。|
|[ArgTraitsHelper 結構](argtraitshelper-structure.md)|有助於定義委派引數的一般特性。|
|[BoolStruct 結構](boolstruct-structure.md)|定義是否 `ComPtr` 正在管理介面的物件存留期。 `BoolStruct`[BoolType （）](comptr-class.md#operator-microsoft-wrl-details-booltype)運算子會在內部使用。|
|[CreatorMap 結構](creatormap-structure.md)|包含如何初始化、註冊及取消註冊物件的相關資訊。|
|[DerefHelper 結構](derefhelper-structure.md)|表示樣板參數的解除引用指標 `T*` 。|
|[EnableIf 結構](enableif-structure.md)|定義第二個樣板參數所指定之類型的資料成員（如果第一個樣板參數評估為） **`true`** 。|
|[FactoryCache 結構](factorycache-structure.md)|包含 Class Factory 的位置，以及識別已註冊 Windows 執行階段或 COM 類別物件的值。|
|[ImplementsBase 結構](implementsbase-structure.md)|用來驗證[Implements 結構](implements-structure.md)中的範本參數類型。|
|[ImplementsHelper 結構](implementshelper-structure.md)|協助執行實[結構。](implements-structure.md)|
|[InterfaceList 結構](interfacelist-structure.md)|用來建立介面的遞迴清單。|
|[InterfaceListHelper 結構](interfacelisthelper-structure.md)|藉 `InterfaceList` 由以遞迴方式套用指定的範本參數引數來建立類型。|
|[InterfaceTraits 結構](interfacetraits-structure.md)|執行介面的一般特性。|
|[InvokeHelper 結構](invokehelper-structure.md)|`Invoke()`根據指定的引數數目和類型，提供方法的執行。|
|[IsBaseOfStrict 結構](isbaseofstrict-structure.md)|測試某個類型是否為另一個類型的基底。|
|[IsSame 結構](issame-structure.md)|測試一個指定的類型是否與另一個指定的類型相同。|
|[Nil 結構](nil-structure.md)|用來表示未指定的選擇性範本參數。|
|[RemoveReference 結構](removereference-structure.md)|從指定的類別樣板參數中，去除參考或右值參考特性。|
|[RuntimeClassBase 結構](runtimeclassbase-structure.md)|用來 `RuntimeClass` 在[Make](make-function.md)函式中偵測。|
|[RuntimeClassBaseT 結構](runtimeclassbaset-structure.md)|提供 helper 方法來進行 `QueryInterface` 作業和取得介面識別碼。|
|[VerifyInheritanceHelper 結構](verifyinheritancehelper-structure.md)|測試某個介面是否衍生自另一個介面。|
|[VerifyInterfaceHelper 結構](verifyinterfacehelper-structure.md)|驗證範本參數所指定的介面是否符合特定需求。|

### <a name="enumerations"></a>列舉

|名稱|說明|
|----------|-----------------|
|[AsyncStatusInternal 列舉](asyncstatusinternal-enumeration.md)|針對非同步作業和列舉的狀態，指定內部列舉之間的對應 `Windows::Foundation::AsyncStatus` 。|

### <a name="functions"></a>函式

|名稱|說明|
|----------|-----------------|
|[ActivationFactoryCallback 函式](activationfactorycallback-function.md)|取得指定之啟用識別碼的啟用 factory。|
|[Move 函式](move-function.md)|將指定的引數從一個位置移動到另一個位置。|
|[RaiseException 函式](raiseexception-function.md)|在呼叫執行緒中引發例外狀況。|
|[Swap 函式（WRL）](swap-function-wrl.md)|交換兩個指定引數的值。|
|[TerminateMap 函式](terminatemap-function.md)|關閉指定模組中的 class factory。|

## <a name="requirements"></a>需求

**標頭：** async .h、corewrappers、ftm、event .h、、implements、internal、module. h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft：： WRL 命名空間](microsoft-wrl-namespace.md)<br/>
[Microsoft：： WRL：：包裝函式命名空間](microsoft-wrl-wrappers-namespace.md)
