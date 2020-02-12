---
title: CComPtr 類別
description: Microsoft C++ ACTIVE TEMPLATE LIBRARY （ATL）類別 CComPtr 的參考指南。
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127401"
---
# <a name="ccomptr-class"></a>CComPtr 類別

用於管理 COM 介面指標的智慧型指標類別。

## <a name="syntax"></a>語法

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>參數

*T*<br/>
COM 介面，指定要儲存之指標的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPtr：： CComPtr](#ccomptr)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComPtr：： operator =](#operator_eq)|指派成員指標的指標。|

## <a name="remarks"></a>備註

ATL 會使用 `CComPtr` 和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)來管理 COM 介面指標。 兩者都是衍生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，而且兩者都執行自動參考計數。

`CComPtr` 和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)類別可以藉由執行自動參考計數，協助消除記憶體流失。  下列函數會執行相同的邏輯作業。 不過，第二個版本可能較不容易發生錯誤，因為它使用 `CComPtr` 類別：

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

在 [Debug build] 中，連結 atlsd.lib 以進行程式碼追蹤。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccomptr"></a>CComPtr：： CComPtr

建構函式。

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>參數

*lp*<br/>
用來初始化介面指標。

*T*<br/>
COM 介面。

### <a name="remarks"></a>備註

接受引數呼叫的函式會在*lp*上 `AddRef`，如果它不是 null 指標。 非 null 擁有的物件會在 CComPtr 物件的銷毀時取得 `Release` 呼叫，或如果將新的物件指派給 CComPtr 物件，則為。

## <a name="operator_eq"></a>CComPtr：： operator =

指派運算子。

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>傳回值

傳回已更新之 `CComPtr` 物件的指標

### <a name="remarks"></a>備註

這項作業會 AddRefs 新的物件，並釋放現有的物件（如果有的話）。

## <a name="see-also"></a>另請參閱

[CComPtr：： CComPtr](#ccomptr)<br/>
[CComQIPtr：： CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[類別總覽](../../atl/atl-class-overview.md)
