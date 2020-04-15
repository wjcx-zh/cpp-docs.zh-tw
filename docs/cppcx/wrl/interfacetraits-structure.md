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
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371363"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*隱形型*<br/>
`Implements`和`RuntimeClass`的介面不會位於受支援的介面指示`ChainInterfaces`的清單中。

## <a name="remarks"></a>備註

實現介面的通用特性。

第二個範本是掩蔽介面的專門化。 第三個範本是 Nil 參數的專門化。

## <a name="members"></a>成員

### <a name="public-typedefs"></a><a name="public-typedefs"></a>公開類型

名稱   | 描述
------ | ------------------------------------------
`Base` | *I0*模板參數的同義詞。

### <a name="public-methods"></a>公用方法

名稱                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[介面特徵::坎卡斯特托](#cancastto)               | 指示指定指標是否可以轉換為指向`Base`的指標。
[介面特徵::CasttoBase](#casttobase)             | 將指定的指標強制轉換為指向`Base`的指標。
[介面特徵::強制未知](#casttounknown)       | 將指定的指標強制轉換為指向`IUnknown`的指標。
[介面特徵::填充帶](#fillarraywithiid) | 將的`Base`介面識別碼分配給索引參數指定的陣列元素。
[介面特徵:驗證](#verify)                     | 驗證`Base`正確派生的。

### <a name="public-constants"></a>公用常數

名稱                                   | 描述
-------------------------------------- | ---------------------------------------------------------------------------------------
[介面特徵::IidCount](#iidcount) | 保存與當前`InterfaceTraits`物件關聯的介面指示數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`InterfaceTraits`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>介面特徵::坎卡斯特托

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*Ptr*<br/>
指向類型的指標的名稱。

*riid*<br/>
的介面`Base`識別碼。

*Ppv*<br/>
如果此操作成功 *,ppv*將指向`Base`指定的 介面。 否則 *,ppv*`nullptr`設定為 。

### <a name="return-value"></a>傳回值

如果此操作成功,並且*ptr*被強制轉換`Base`為指向的指標,**則為 true。** 否則,**假**。

### <a name="remarks"></a>備註

指示指定指標是否可以轉換為指向`Base`的指標。

有關的詳細資訊`Base`,請參閱[公共類型防禦區](#public-typedefs)部分。

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>介面特徵::CasttoBase

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數*ptr*的類型。

*Ptr*<br/>
指向類型*T*的指標。

### <a name="return-value"></a>傳回值

`Base` 的指標。

### <a name="remarks"></a>備註

將指定的指標強制轉換為指向`Base`的指標。

有關的詳細資訊`Base`,請參閱[公共類型防禦區](#public-typedefs)部分。

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>介面特徵::強制未知

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數*ptr*的類型。

*Ptr*<br/>
指向類型*T 的*指標。

### <a name="return-value"></a>傳回值

指向派生的 I`Base`未知項的指標。

### <a name="remarks"></a>備註

將指定的指標強制轉換為指向`IUnknown`的指標。

有關的詳細資訊`Base`,請參閱[公共類型防禦區](#public-typedefs)部分。

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>介面特徵::填充帶

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*指數*<br/>
指向包含零基索引值的欄位的指標。

*伊德*<br/>
介面指示的陣列。

### <a name="remarks"></a>備註

將的`Base`介面識別碼分配給索引參數指定的陣列元素。

與此 API 的名稱相反,只修改一個陣組元素;而不是整個陣列。

有關的詳細資訊`Base`,請參閱[公共類型防禦區](#public-typedefs)部分。

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>介面特徵::IidCount

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>備註

保存與當前`InterfaceTraits`物件關聯的介面指示數。

## <a name="interfacetraitsverify"></a><a name="verify"></a>介面特徵:驗證

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>備註

驗證`Base`正確派生的。

有關的詳細資訊`Base`,請參閱[公共類型防禦區](#public-typedefs)部分。
