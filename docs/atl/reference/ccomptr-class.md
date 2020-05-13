---
title: CComPtr 類別
description: Microsoft C++活動範本庫 (ATL) 類 CComPtr 的參考指南。
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327530"
---
# <a name="ccomptr-class"></a>CComPtr 類別

用於管理 COM 介面指標的智慧指標類。

## <a name="syntax"></a>語法

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>參數

*T*<br/>
指定要儲存的指標類型的 COM 介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPtr:CComPtr](#ccomptr)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComPtr::運算符 |](#operator_eq)|分配指向成員指標的指標。|

## <a name="remarks"></a>備註

ATL`CComPtr`使用[CComQIPtr](../../atl/reference/ccomqiptr-class.md)來管理 COM 介面指標。 兩者都來自[CComPtrBase,](../../atl/reference/ccomptrbase-class.md)並且都執行自動引用計數。

`CComPtr`和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)類可以通過執行自動引用計數來説明消除記憶體洩漏。  以下函數都執行相同的邏輯操作。 但是,第二個版本可能不太容易出錯,因為它使用類`CComPtr`:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

在除錯版本中,連結atlsd.lib進行代碼追蹤。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr:CComPtr

建構函式。

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>參數

*lp*<br/>
用於初始化介面指標。

*T*<br/>
COM 介面。

### <a name="remarks"></a>備註

在`AddRef`*lp*上獲取參數調用的構造函數,如果它不是空指標。 非空擁有的物件獲取對 CComPtr 物件的`Release`破壞的調用,或者如果將新物件分配給 CComPtr 物件。

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::運算符 |

指派運算子。

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>傳回值

傳回更新`CComPtr`物件的指標

### <a name="remarks"></a>備註

此操作 AddRef 新物件並釋放現有物件(如果存在)。

## <a name="see-also"></a>另請參閱

[CComPtr:CComPtr](#ccomptr)<br/>
[CComQIPtr:CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[類別概觀](../../atl/atl-class-overview.md)
