---
title: "Microsoft::WRL::Details 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Microsoft::WRL::Details 命名空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
namespace Microsoft::WRL::Details;  
```  
  
## <a name="members"></a>Members  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[ComPtrRef 類別](../windows/comptrref-class.md)|表示參考物件的型別 ComPtr \< T>。|  
|[ComPtrRefBase 類別](../windows/comptrrefbase-class.md)|表示基底類別 [ComPtrRef](../windows/comptrref-class.md) 類別。|  
|[DontUseNewUseMake 類別](../windows/dontusenewusemake-class.md)|防止使用運算子 `new` 中 `RuntimeClass`。 因此，您必須使用 [讓函式](../windows/make-function.md) 改。|  
|[EventTargetArray 類別](../windows/eventtargetarray-class.md)|表示事件處理常式的陣列。|  
|[MakeAllocator 類別](../windows/makeallocator-class.md)|可啟動類別，使用或不支援弱式參考，會配置記憶體。|  
|[ModuleBase 類別](../windows/modulebase-class.md)|表示基底類別 [模組](../windows/module-class.md) 類別。|  
|[RemoveIUnknown 類別](../windows/removeiunknown-class.md)|建立類型，相當於 `IUnknown`-根據型別，但有非虛擬 `QueryInterface`, ，`AddRef`, ，和 `Release` 方法。|  
|[WeakReference 類別](../windows/weakreference-class1.md)|代表 *弱式參考* ，可以搭配 Windows 執行階段或傳統 com 使用。 弱式參考代表不一定可存取的物件。|  
  
### <a name="structures"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|[ArgTraits 結構](../windows/argtraits-structure.md)|會在指定的委派宣告介面和匿名的成員函式具有指定的參數數目。|  
|[ArgTraitsHelper 結構](../windows/argtraitshelper-structure.md)|可協助定義委派引數的一般的特性。|  
|[BoolStruct 結構](../windows/boolstruct-structure.md)|定義是否 ComPtr 管理介面的物件存留期。 BoolStruct 會在內部使用 [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) 運算子。|  
|[CreatorMap 結構](../windows/creatormap-structure.md)|包含如何初始化、 註冊及取消註冊物件的相關資訊。|  
|[DerefHelper 結構](../windows/derefhelper-structure.md)|代表取值的指標 `T*` 樣板參數。|  
|[EnableIf 結構](../windows/enableif-structure.md)|如果第一個範本參數評估為第二個範本參數所指定之型別的資料成員會定義 `true`。|  
|[FactoryCache 結構](../windows/factorycache-structure.md)|包含一個 class factory 和值，識別已註冊的位置 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 或 COM 類別物件。|  
|[ImplementsBase 結構](../windows/implementsbase-structure.md)|用來驗證範本參數的型別中 [Implements 結構](../windows/implements-structure.md)。|  
|[ImplementsHelper 結構](../windows/implementshelper-structure.md)|可協助實作 [實作](../windows/implements-structure.md) 結構。|  
|[InterfaceList 結構](../windows/interfacelist-structure.md)|用來建立遞迴清單的介面。|  
|[InterfaceListHelper 結構](../windows/interfacelisthelper-structure.md)|建置 `InterfaceList` 以遞迴方式套用指定的範本參數引數的型別。|  
|[InterfaceTraits 結構](../windows/interfacetraits-structure.md)|實作的介面的一般特性。|  
|[InvokeHelper 結構](../windows/invokehelper-structure.md)|提供根據指定的數目和類型的引數的 invoke （） 方法的實作。|  
|[IsBaseOfStrict 結構](../windows/isbaseofstrict-structure.md)|測試某個類型是否為另一個類型的基底。|  
|[IsSame 結構](../windows/issame-structure.md)|其中一個指定的型別是否是與另一個相同的測試指定之類型。|  
|[Nil 結構](../windows/nil-structure.md)|用來指示未指定選擇性的範本參數。|  
|[RemoveReference 結構](../windows/removereference-structure.md)|去除將參考或右值參考的功能，從指定的類別樣板參數。|  
|[RuntimeClassBase 結構](../windows/runtimeclassbase-structure.md)|用來偵測 `RuntimeClass` 中 [讓](../windows/make-function.md) 函式。|  
|[RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)|提供 helper 方法以 `QueryInterface` 作業和取得的介面識別碼。|  
|[VerifyInheritanceHelper 結構](../windows/verifyinheritancehelper-structure.md)|測試是否有一個介面衍生自另一個介面。|  
|[VerifyInterfaceHelper 結構](../windows/verifyinterfacehelper-structure.md)|確認範本參數所指定的介面符合特定需求。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|說明|  
|----------|-----------------|  
|[AsyncStatusInternal 列舉](../windows/asyncstatusinternal-enumeration.md)|指定狀態的非同步作業的內部列舉型別之間的對應和 **Windows::Foundation::AsyncStatus** 列舉型別。|  
  
### <a name="functions"></a>函式  
  
|名稱|說明|  
|----------|-----------------|  
|[ActivationFactoryCallback 函式](../windows/activationfactorycallback-function.md)|取得啟動 factory 做為指定的啟用識別碼。|  
|[Move 函式](../windows/move-function.md)|將指定的引數從一個位置移到另一個。|  
|[RaiseException 函式](../windows/raiseexception-function.md)|引發例外狀況在呼叫的執行緒。|  
|[Swap 函式 （Windows 執行階段 c + + 樣板程式庫）](../windows/swap-function-windows-runtime-cpp-template-library.md)|交換兩個指定的引數的值。|  
|[TerminateMap 函式](../windows/terminatemap-function.md)|關閉指定的模組中的類別處理站。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h  
  
 **命名空間︰** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)