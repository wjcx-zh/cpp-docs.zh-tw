---
title: RuntimeClassBaseT 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375726"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>參數

*執行時類別類型T*<br/>
指定一個或多個[執行時類類型](runtimeclasstype-enumeration.md)枚舉器的標誌欄位。

## <a name="remarks"></a>備註

為`QueryInterface`操作和獲取介面識別器提供説明程式方法。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------
[執行時類基礎::AsIID](#asiid)                           | 檢索指向指定介面 ID 的指標。
[執行時類基礎::獲取已實現 IIDS](#getimplementediids) | 檢索由指定類型實現的介面指示的陣列。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`RuntimeClassBaseT`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>執行時類基礎::AsIID

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>參數

*T*<br/>
實現參數*riid*指定的介面 ID 的類型。

*實現*<br/>
樣本參數*T*指定的類型的變數。

*riid*<br/>
要檢索的介面 ID。

*ppvObject*<br/>
如果此操作成功,則指向參數*riid*指定的介面的指標指向指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

檢索指向指定介面 ID 的指標。

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>執行時類基礎::獲取已實現 IIDS

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>參數

*T*<br/>
*實現*參數的類型。

*實現*<br/>
指向參數*T*指定的類型的指標。

*iid( Iid) Count*<br/>
要檢索的介面指示的最大數量。

*伊德*<br/>
如果此操作成功完成,則按*類型 T*實現的介面 I 的陣列。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

檢索由指定類型實現的介面指示的陣列。
