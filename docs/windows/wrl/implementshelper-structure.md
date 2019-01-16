---
title: ImplementsHelper 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: 250a59152e9b41eb48c453caaa696fdc8ca3d3b4
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335679"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>參數

*RuntimeClassFlagsT*<br/>
指定一或多個旗標欄位[RuntimeClassType](runtimeclasstype-enumeration.md)列舉值。

*ILst*<br/>
介面識別碼的清單。

*IsDelegateToClass*<br/>
指定 **，則為 true**如果目前的執行個體`Implements`的基底類別中的第一個介面識別碼*ILst*; 否則**false**。

## <a name="remarks"></a>備註

可協助實作[實作](implements-structure.md)結構。

此範本會周遊之介面的清單，並將它們加入做為基底類別，以及啟用所需的資訊`QueryInterface`。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                    | 描述
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | 取得指標的指定的介面 id。
[ImplementsHelper::CastToUnknown](#casttounknown)       | 取得指標的基礎`IUnknown`目前的介面`Implements`結構。
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | 插入至指定的陣列項目目前的第零個範本參數所指定的介面識別碼。
[ImplementsHelper::IidCount](#iidcount)                 | 會保留在目前已實作的介面 Id 號碼`Implements`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`ImplementsHelper`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="cancastto"></a>ImplementsHelper::CanCastTo

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
參考介面識別碼。

*ppv*<br/>
如果這項作業成功時，所指定之介面指標*riid*或是*iid*。

*iid*<br/>
參考介面識別碼。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

取得指標的指定的介面 id。

## <a name="casttounknown"></a>ImplementsHelper::CastToUnknown

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

指向基礎`IUnknown`介面。

### <a name="remarks"></a>備註

取得指標的基礎`IUnknown`目前的介面`Implements`結構。

## <a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>參數

*index*<br/>
以零為起始的索引，指出起始的陣列項目，這項作業。 這項作業完成時， *index*都會遞增 1。

*iids*<br/>
Iid 類型的陣列。

### <a name="remarks"></a>備註

插入至指定的陣列項目目前的第零個範本參數所指定的介面識別碼。

## <a name="iidcount"></a>ImplementsHelper::IidCount

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>備註

會保留在目前已實作的介面 Id 號碼`Implements`物件。
