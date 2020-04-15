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
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371390"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>參數

*執行時類別標誌T*<br/>
指定一個或多個[執行時類類型](runtimeclasstype-enumeration.md)枚舉器的標誌欄位。

*ILst*<br/>
介面指示清單。

*是委託類*<br/>
如果`Implements`目前 實體是*ILst*中第一個介面 ID 的基項,請**指定 true;** 否則,**假**。

## <a name="remarks"></a>備註

幫助實現[實現器](implements-structure.md)結構。

此範本遍歷介面清單,並將它們添加為基類,並作為啟用`QueryInterface`所需的資訊。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                    | 描述
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[實現幫助器::坎卡斯特托](#cancastto)               | 獲取指向指定介面 ID 的指標。
[實現說明器:Castto 未知](#casttounknown)       | 獲取指向當前`IUnknown``Implements`結構的基礎介面的指標。
[實現說明器::fillarray 與 Id](#fillarraywithiid) | 將當前零點範本參數指定的介面 ID 插入指定的陣列元素。
[實現說明器::IidCount](#iidcount)                 | 保存當前`Implements`物件中已實現的介面指示數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ImplementsHelper`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>實現幫助器::坎卡斯特托

支援 WRL 基礎結構,不打算直接從代碼中使用。

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
對介面 ID 的引用。

*Ppv*<br/>
如果此操作成功,則指向*riid*或*iid*指定的介面的指標。

*Iid*<br/>
對介面 ID 的引用。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

獲取指向指定介面 ID 的指標。

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>實現說明器:Castto 未知

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>傳回值

指向基礎`IUnknown`介面的指標。

### <a name="remarks"></a>備註

獲取指向當前`IUnknown``Implements`結構的基礎介面的指標。

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>實現說明器::fillarray 與 Id

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>參數

*指數*<br/>
一個基於零的索引,指示此操作的起始陣組元素。 此動作完成後,*索引*將遞增 1。

*伊德*<br/>
IID 類型的陣列。

### <a name="remarks"></a>備註

將當前零點範本參數指定的介面 ID 插入指定的陣列元素。

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>實現說明器::IidCount

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>備註

保存當前`Implements`物件中已實現的介面指示數。
