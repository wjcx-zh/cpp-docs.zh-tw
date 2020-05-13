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
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371414"
---
# <a name="implements-structure"></a>Implements 結構

實現`QueryInterface`和`GetIid`指定介面。

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
第零個介面 ID。 (必要)

*I1*<br/>
第一個介面 ID。 (選用)

*I2*<br/>
第二個介面 ID。 (選用)

*I3*<br/>
第三個介面 ID。 (選用)

*I4*<br/>
第四個介面 ID。 (選用)

*I5*<br/>
第五個介面 ID。 (選用)

*I6*<br/>
第六個介面 ID。 (選用)

*I7*<br/>
第七個介面 ID。 (選用)

*I8*<br/>
第八個介面 ID。 (選用)

*I9*<br/>
第九個介面 ID。 (選用)

*標誌*<br/>
類的配置標誌。 在[運行時類標誌](runtimeclassflags-structure.md)結構中指定的一個或多個[運行時類類型](runtimeclasstype-enumeration.md)枚舉。

## <a name="remarks"></a>備註

派生自 和 的指定介面和實現説明程式`QueryInterface``GetIid`範本 的清單。

每個*I0*到*I9*介面參數`IUnknown`必須`IInspectable`派生自 ,或[連結口](chaininterfaces-structure.md)範本。 *標誌*參數確定是否`IUnknown`為`IInspectable`或生成支援。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

| 名稱        | 描述                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同義字。 |

### <a name="protected-methods"></a>保護方法

| 名稱                                              | 描述                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [實現::坎卡斯特托](#cancastto)               | 獲取指向指定介面的指標。                                                                    |
| [實作::強制未知](#casttounknown)       | 獲取指向基礎`IUnknown`介面的指標。                                                        |
| [實現::用 Iid 填充](#fillarraywithiid) | 將當前零點範本參數指定的介面 ID 插入指定的陣列元素。 |

### <a name="protected-constants"></a>受保護的常量

| 名稱                              | 描述                                    |
| --------------------------------- | ---------------------------------------------- |
| [實作:IdCount](#iidcount) | 保存已實現的介面指示數。 |

## <a name="inheritance-hierarchy"></a>繼承階層架構

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間：** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>實現::坎卡斯特托

獲取指向指定介面的指標。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*<br/>
對介面 ID 的引用。

*Ppv*<br/>
如果成功,則指向*riid*指定的介面的指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,指示錯誤的 HRESULT,如E_NOINTERFACE。

### <a name="remarks"></a>備註

這是執行查詢介面操作的內部説明器函數。

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>實作::強制未知

獲取指向基礎`IUnknown`介面的指標。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

此操作始終成功並返回`IUnknown`指標。

### <a name="remarks"></a>備註

內部幫助器功能。

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>實現::用 Iid 填充

將當前零點範本參數指定的介面 ID 插入指定的陣列元素。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*指數*<br/>
一個基於零的索引,指示此操作的起始陣組元素。 此動作完成後,*索引*將遞增 1。

*伊德*<br/>
IID 類型的陣列。

### <a name="remarks"></a>備註

內部幫助器功能。

## <a name="implementsiidcount"></a><a name="iidcount"></a>實作:IdCount

保存已實現的介面指示數。

```cpp
static const unsigned long IidCount;
```
