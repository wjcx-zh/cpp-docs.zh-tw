---
title: InterfaceTraits 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: c08c6e8bbcc16120dd44da69a2933fc3ec42f387
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216566"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>參數

*I0*<br/>
介面的名稱。

*CloakedType*<br/>
針對 `RuntimeClass` 、 `Implements` 和 `ChainInterfaces` ，此介面不會出現在支援的介面識別碼清單中。

## <a name="remarks"></a>備註

執行介面的一般特性。

第二個範本是已遮蓋介面的特製化。 第三個範本是 Nil 參數的特製化。

## <a name="members"></a>成員

### <a name="public-typedefs"></a><a name="public-typedefs"></a>公用 Typedef

名稱   | 說明
------ | ------------------------------------------
`Base` | *I0*範本參數的同義字。

### <a name="public-methods"></a>公用方法

名稱                                                   | 說明
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits：： CanCastTo](#cancastto)               | 指出是否可以將指定的指標轉換為的指標 `Base` 。
[InterfaceTraits：： CastToBase](#casttobase)             | 將指定的指標轉換為的指標 `Base` 。
[InterfaceTraits：： CastToUnknown](#casttounknown)       | 將指定的指標轉換為的指標 `IUnknown` 。
[InterfaceTraits：： FillArrayWithIid](#fillarraywithiid) | 將的介面識別碼指派 `Base` 給索引引數所指定的陣列元素。
[InterfaceTraits：： Verify](#verify)                     | 驗證 `Base` 是否已正確衍生。

### <a name="public-constants"></a>公用常數

名稱                                   | 說明
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits：： IidCount](#iidcount) | 保留與目前物件相關聯的介面識別碼數目 `InterfaceTraits` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`InterfaceTraits`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits：： CanCastTo

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*ptr*<br/>
類型的指標名稱。

*riid*<br/>
的介面識別碼 `Base` 。

*ppv*<br/>
如果這項作業成功， *ppv*會指向所指定的介面 `Base` 。 否則， *ppv*會設定為 **`nullptr`** 。

### <a name="return-value"></a>傳回值

**`true`** 如果此作業成功，且*ptr*轉換成的指標， `Base` 則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

指出是否可以將指定的指標轉換為的指標 `Base` 。

如需的詳細資訊 `Base` ，請參閱[公用 typedef](#public-typedefs)一節。

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits：： CastToBase

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數*ptr*的類型。

*ptr*<br/>
*T*類型的指標。

### <a name="return-value"></a>傳回值

`Base` 的指標。

### <a name="remarks"></a>備註

將指定的指標轉換為的指標 `Base` 。

如需的詳細資訊 `Base` ，請參閱[公用 typedef](#public-typedefs)一節。

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits：： CastToUnknown

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數*ptr*的類型。

*ptr*<br/>
類型*T*的指標。

### <a name="return-value"></a>傳回值

衍生之 IUnknown 的指標 `Base` 。

### <a name="remarks"></a>備註

將指定的指標轉換為的指標 `IUnknown` 。

如需的詳細資訊 `Base` ，請參閱[公用 typedef](#public-typedefs)一節。

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits：： FillArrayWithIid

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*指數*<br/>
包含以零為基底之索引值的欄位指標。

*iid*<br/>
介面識別碼的陣列。

### <a name="remarks"></a>備註

將的介面識別碼指派 `Base` 給索引引數所指定的陣列元素。

相反于此 API 的名稱，只會修改一個陣列元素;不是整個陣列。

如需的詳細資訊 `Base` ，請參閱[公用 typedef](#public-typedefs)一節。

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits：： IidCount

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>備註

保留與目前物件相關聯的介面識別碼數目 `InterfaceTraits` 。

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits：： Verify

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>備註

驗證 `Base` 是否已正確衍生。

如需的詳細資訊 `Base` ，請參閱[公用 typedef](#public-typedefs)一節。
