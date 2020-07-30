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
ms.openlocfilehash: d7908670b67df7dbf7b2b74e98f8b59cf30f8e96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184939"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>參數

*RuntimeClassFlagsT*<br/>
旗標的欄位，指定一或多個[RuntimeClassType](runtimeclasstype-enumeration.md)列舉值。

*ILst*<br/>
介面識別碼的清單。

*IsDelegateToClass*<br/>
指定 **`true`** 目前的實例 `Implements` 是否為*ILst*中第一個介面識別碼的基類，否則為 **`false`** 。

## <a name="remarks"></a>備註

協助執行實[結構。](implements-structure.md)

此範本會遍歷介面的清單，並將它們新增為基類，以及做為啟用所需的資訊 `QueryInterface` 。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                    | 說明
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper：： CanCastTo](#cancastto)               | 取得指定介面識別碼的指標。
[ImplementsHelper：： CastToUnknown](#casttounknown)       | 取得目前結構之基礎介面的指標 `IUnknown` `Implements` 。
[ImplementsHelper：： FillArrayWithIid](#fillarraywithiid) | 將目前預備樣板參數所指定的介面識別碼插入指定的陣列元素中。
[ImplementsHelper：： IidCount](#iidcount)                 | 保留目前物件中實作為介面識別碼的數目 `Implements` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ImplementsHelper`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper：： CanCastTo

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

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
介面識別碼的參考。

*ppv*<br/>
如果此作業成功，則為*riid*或*iid*所指定之介面的指標。

*iid*<br/>
介面識別碼的參考。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

取得指定介面識別碼的指標。

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper：： CastToUnknown

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

基礎介面的指標 `IUnknown` 。

### <a name="remarks"></a>備註

取得目前結構之基礎介面的指標 `IUnknown` `Implements` 。

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper：： FillArrayWithIid

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>參數

*指數*<br/>
以零為基底的索引，表示此作業的起始陣列元素。 當此作業完成時，*索引*會遞增1。

*iid*<br/>
Iid 類型的陣列。

### <a name="remarks"></a>備註

將目前預備樣板參數所指定的介面識別碼插入指定的陣列元素中。

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper：： IidCount

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>備註

保留目前物件中實作為介面識別碼的數目 `Implements` 。
