---
title: ComPtr 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a20dd5e2fb43dd5caae7a5185260d8c88637d33
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597958"
---
# <a name="comptr-class"></a>ComPtr 類別

建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 **ComPtr**自動維護基礎介面指標的參考計數，並參考計數歸零時釋放介面。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>參數

*T*  
介面可**ComPtr**表示。

*U*  
類別目前**ComPtr**為 friend。 (使用這個參數的範本會受到保護)。

## <a name="remarks"></a>備註

`ComPtr<>` 宣告代表基礎介面指標的類型。 使用 `ComPtr<>`來宣告變數，然後使用 箭號成員存取運算子 (`->`) 來存取介面成員函式。

如需智慧型指標的詳細資訊，請參閱的 < COM 智慧型指標 > 一節[COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices)MSDN Library 中的主題。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`InterfaceType`|所指定之類型的同義字*T*樣板參數。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[ComPtr::ComPtr 建構函式](../windows/comptr-comptr-constructor.md)|初始化的新執行個體**ComPtr**類別。 多載提供預設、複製、移動和轉換建構函式。|
|[ComPtr::~ComPtr 解構函式](../windows/comptr-tilde-comptr-destructor.md)|取消初始化的執行個體**ComPtr**。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ComPtr::As 方法](../windows/comptr-as-method.md)|傳回**ComPtr**物件，表示指定的範本參數所識別的介面。|
|[ComPtr::AsIID 方法](../windows/comptr-asiid-method.md)|傳回**ComPtr**物件，表示指定的介面識別碼所識別的介面|
|[ComPtr::AsWeak 方法](../windows/comptr-asweak-method.md)|擷取目前物件的弱式參考。|
|[ComPtr::Attach 方法](../windows/comptr-attach-method.md)|將這**ComPtr**與目前的範本類型參數所指定的介面類型。|
|[ComPtr::CopyTo 方法](../windows/comptr-copyto-method.md)|複製目前或指定相關聯的介面與這個**ComPtr**到指定的輸出指標。|
|[ComPtr::Detach 方法](../windows/comptr-detach-method.md)|解除這**ComPtr**從它所代表的介面。|
|[ComPtr::Get 方法](../windows/comptr-get-method.md)|擷取與此相關聯的介面指標**ComPtr**。|
|[ComPtr::GetAddressOf 方法](../windows/comptr-getaddressof-method.md)|擷取位址[ptr_](../windows/comptr-ptr-data-member.md)資料成員，其中包含這所代表之介面的指標**ComPtr**。|
|[ComPtr::ReleaseAndGetAddressOf 方法](../windows/comptr-releaseandgetaddressof-method.md)|釋放與這個相關聯的介面**ComPtr** ，然後擷取的地址[ptr_](../windows/comptr-ptr-data-member.md)資料成員，其中包含已釋放之介面的指標。|
|[ComPtr::Reset](../windows/comptr-reset.md)|釋放與此相關聯的介面指標的所有參考**ComPtr**。|
|[ComPtr::Swap 方法](../windows/comptr-swap-method.md)|交換目前所管理之介面**ComPtr**與管理指定之介面**ComPtr**。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[ComPtr::InternalAddRef 方法](../windows/comptr-internaladdref-method.md)|與此相關聯的介面的參考計數遞增**ComPtr**。|
|[ComPtr::InternalRelease 方法](../windows/comptr-internalrelease-method.md)|執行與此相關聯的介面上的 COM 釋放作業**ComPtr**。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[ComPtr::operator Microsoft::WRL::Details::BoolType 運算子](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|指出是否**ComPtr**管理介面的物件存留期。|
|[ComPtr::operator& 運算子](../windows/comptr-operator-ampersand-operator.md)|擷取目前的地址**ComPtr**。|
|[ComPtr::operator= 運算子](../windows/comptr-operator-assign-operator.md)|將值指派給目前**ComPtr**。|
|[ComPtr::operator-> 運算子](../windows/comptr-operator-arrow-operator.md)|擷取目前範本參數所指定之類型的指標。|
|[ComPtr::operator== 運算子](../windows/comptr-operator-equality-operator.md)|指出兩個**ComPtr**物件是否相等。|
|[ComPtr::operator!= 運算子](../windows/comptr-operator-inequality-operator.md)|指出兩個**ComPtr**物件是否不相等。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[ComPtr::ptr_ 資料成員](../windows/comptr-ptr-data-member.md)|包含相關聯，並管理由這個介面的指標**ComPtr**。|

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtr`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)