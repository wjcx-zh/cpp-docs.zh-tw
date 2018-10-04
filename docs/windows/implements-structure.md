---
title: 實作結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc993dc1ebe0c5f1ab11409fcecee9b6cdefdaae
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788770"
---
# <a name="implements-structure"></a>Implements 結構

Implements`QueryInterface`和`GetIid`指定介面。

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
第零個介面 id。 （必要）

*I1*<br/>
第一個介面 id。 (選擇項)

*I2*<br/>
第二個介面 id。 (選擇項)

*I3*<br/>
第三個介面 id。 (選擇項)

*I4*<br/>
第四個介面 id。 (選擇項)

*I5 中*<br/>
第五個介面 id。 (選擇項)

*I6*<br/>
第六個介面 id。 (選擇項)

*I7*<br/>
第七個介面 id。 (選擇項)

*I8*<br/>
第八個介面 id。 (選擇項)

*I9*<br/>
第九個介面 id。 (選擇項)

*flags*<br/>
此類別的組態旗標。 一或多個[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)中所指定的列舉型別[RuntimeClassFlags](../windows/runtimeclassflags-structure.md)結構。

## <a name="remarks"></a>備註

衍生自指定之介面的清單，並實作協助程式範本`QueryInterface`和`GetIid`。

每個*I0*透過*I9*介面參數必須衍生自`IUnknown`， `IInspectable`，或[ChainInterfaces](../windows/chaininterfaces-structure.md)範本。 *旗標*參數會決定是否產生支援`IUnknown`或`IInspectable`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

| 名稱        | 描述                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同義字。 |

### <a name="protected-methods"></a>保護方法

| 名稱                                              | 描述                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements:: cancastto](#cancastto)               | 取得指定的介面指標。                                                                    |
| [Implements:: casttounknown](#casttounknown)       | 取得指標基礎`IUnknown`介面。                                                        |
| [Implements:: fillarraywithiid](#fillarraywithiid) | 插入至指定的陣列項目目前的第零個範本參數所指定的介面識別碼。 |

### <a name="protected-constants"></a>受保護的常數

| 名稱                              | 描述                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements:: iidcount](#iidcount) | 保留實作的介面識別碼的數目。 |

## <a name="inheritance-hierarchy"></a>繼承階層

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="cancastto"></a>Implements:: cancastto

取得指定的介面指標。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
參考介面識別碼。

*ppv*<br/>
如果成功，介面的指標所指定*riid*。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，HRESULT，表示錯誤，例如 E_NOINTERFACE。

### <a name="remarks"></a>備註

這是執行 QueryInterface 作業的內部協助程式函式。

## <a name="casttounknown"></a>Implements:: casttounknown

取得指標基礎`IUnknown`介面。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

這項作業一定成功，並傳回`IUnknown`指標。

### <a name="remarks"></a>備註

內部 helper 函式。

## <a name="fillarraywithiid"></a>Implements:: fillarraywithiid

插入至指定的陣列項目目前的第零個範本參數所指定的介面識別碼。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*index*<br/>
以零為起始的索引，指出起始的陣列項目，這項作業。 這項作業完成時， *index*都會遞增 1。

*iid*<br/>
IID 類型的陣列。

### <a name="remarks"></a>備註

內部 helper 函式。

## <a name="iidcount"></a>Implements:: iidcount

保留實作的介面識別碼的數目。

```cpp
static const unsigned long IidCount;
```
