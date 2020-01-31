---
title: Implements 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821853"
---
# <a name="implements-structure"></a>Implements 結構

針對指定的介面，執行 `QueryInterface` 和 `GetIid`。

## <a name="syntax"></a>語法

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>參數

*I0*<br/>
預備介面識別碼。 不必

*I1*<br/>
第一個介面識別碼。 (可省略)

*I2*<br/>
第二個介面識別碼。 (可省略)

*I3*<br/>
第三個介面識別碼。 (可省略)

*I4*<br/>
第四個介面識別碼。 (可省略)

*I5*<br/>
第五個介面識別碼。 (可省略)

*I6*<br/>
第六個介面識別碼。 (可省略)

*I7*<br/>
第七個介面識別碼。 (可省略)

*I8*<br/>
第八個介面識別碼。 (可省略)

*I9-7xxx*<br/>
第九個介面識別碼。 (可省略)

*flags*<br/>
類別的設定旗標。 [RuntimeClassFlags](runtimeclassflags-structure.md)結構中所指定的一或多個[RuntimeClassType](runtimeclasstype-enumeration.md)列舉。

## <a name="remarks"></a>備註

衍生自指定介面的清單，並執行 `QueryInterface` 和 `GetIid`的 helper 範本。

每個*I0*至*i9-7xxx*介面參數都必須衍生自 `IUnknown`、`IInspectable`或[ChainInterfaces](chaininterfaces-structure.md)範本。 *Flags*參數會決定是否針對 `IUnknown` 或 `IInspectable`產生支援。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

| Name        | 描述                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同義字。 |

### <a name="protected-methods"></a>保護方法

| Name                                              | 描述                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements：： CanCastTo](#cancastto)               | 取得指定介面的指標。                                                                    |
| [Implements：： CastToUnknown](#casttounknown)       | 取得基礎 `IUnknown` 介面的指標。                                                        |
| [Implements：： FillArrayWithIid](#fillarraywithiid) | 將目前預備樣板參數所指定的介面識別碼插入指定的陣列元素中。 |

### <a name="protected-constants"></a>受保護的常數

| Name                              | 描述                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements：： IidCount](#iidcount) | 保留實作為介面識別碼的數目。 |

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="cancastto"></a>Implements：： CanCastTo

取得指定介面的指標。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼的參考。

*ppv*<br/>
如果成功，則為*riid*所指定之介面的指標。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，就是指出錯誤的 HRESULT，例如 E_NOINTERFACE。

### <a name="remarks"></a>備註

這是執行 QueryInterface 作業的內部 helper 函式。

## <a name="casttounknown"></a>Implements：： CastToUnknown

取得基礎 `IUnknown` 介面的指標。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

此作業一律會成功，並傳回 `IUnknown` 的指標。

### <a name="remarks"></a>備註

內部 helper 函式。

## <a name="fillarraywithiid"></a>Implements：： FillArrayWithIid

將目前預備樣板參數所指定的介面識別碼插入指定的陣列元素中。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*index*<br/>
以零為基底的索引，表示此作業的起始陣列元素。 當此作業完成時，*索引*會遞增1。

*iid*<br/>
IID 類型的陣列。

### <a name="remarks"></a>備註

內部 helper 函式。

## <a name="iidcount"></a>Implements：： IidCount

保留實作為介面識別碼的數目。

```cpp
static const unsigned long IidCount;
```
