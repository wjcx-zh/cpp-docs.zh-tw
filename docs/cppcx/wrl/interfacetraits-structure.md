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
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784608"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
針對`RuntimeClass`，`Implements`和`ChainInterfaces`，不會在清單中的介面支援的介面識別碼。

## <a name="remarks"></a>備註

實作的介面的一般特性。

第二個範本是特製化隱匿的介面。 第三個範本是特製化 Nil 參數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>Public Typedefs

名稱   | 描述
------ | ------------------------------------------
`Base` | 同義字*I0*樣板參數。

### <a name="public-methods"></a>公用方法

名稱                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | 指出指定的指標是否可以轉換成指標`Base`。
[InterfaceTraits::CastToBase](#casttobase)             | 轉換指標的指定的指標`Base`。
[InterfaceTraits::CastToUnknown](#casttounknown)       | 轉換指標的指定的指標`IUnknown`。
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | 介面 ID 指派為`Base`索引引數所指定的陣列元素。
[InterfaceTraits::Verify](#verify)                     | 確認`Base`正確衍生。

### <a name="public-constants"></a>公用常數

名稱                                   | 描述
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | 保存的介面識別碼相關聯的目前數目`InterfaceTraits`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`InterfaceTraits`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="cancastto"></a>InterfaceTraits::CanCastTo

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
類型的指標的名稱。

*riid*<br/>
介面 ID `Base`。

*ppv*<br/>
如果這項作業成功， *ppv*指向所指定之介面`Base`。 否則，請*ppv*設定為`nullptr`。

### <a name="return-value"></a>傳回值

**則為 true**這項作業成功時並*ptr*轉換成指標`Base`，否則**false**。

### <a name="remarks"></a>備註

指出指定的指標是否可以轉換成指標`Base`。

如需詳細資訊`Base`，請參閱 <<c2> [ 公用 Typedefs](#public-typedefs)一節。

## <a name="casttobase"></a>InterfaceTraits::CastToBase

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數的型別*ptr*。

*ptr*<br/>
類型指標*T*。

### <a name="return-value"></a>傳回值

指標`Base`。

### <a name="remarks"></a>備註

轉換指標的指定的指標`Base`。

如需詳細資訊`Base`，請參閱 <<c2> [ 公用 Typedefs](#public-typedefs)一節。

## <a name="casttounknown"></a>InterfaceTraits::CastToUnknown

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數的型別*ptr*。

*ptr*<br/>
類型指標*T*。

### <a name="return-value"></a>傳回值

IUnknown 指標從中`Base`衍生。

### <a name="remarks"></a>備註

轉換指標的指定的指標`IUnknown`。

如需詳細資訊`Base`，請參閱 <<c2> [ 公用 Typedefs](#public-typedefs)一節。

## <a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*index*<br/>
指標，包含以零為起始的索引值的欄位。

*iids*<br/>
介面識別碼的陣列。

### <a name="remarks"></a>備註

介面 ID 指派為`Base`索引引數所指定的陣列元素。

與此 API 的名稱，只有一個陣列項目遭到修改;不完整的陣列。

如需詳細資訊`Base`，請參閱 <<c2> [ 公用 Typedefs](#public-typedefs)一節。

## <a name="iidcount"></a>InterfaceTraits::IidCount

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>備註

保存的介面識別碼相關聯的目前數目`InterfaceTraits`物件。

## <a name="verify"></a>InterfaceTraits::Verify

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>備註

確認`Base`正確衍生。

如需詳細資訊`Base`，請參閱 <<c2> [ 公用 Typedefs](#public-typedefs)一節。
