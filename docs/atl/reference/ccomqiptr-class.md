---
title: CComQIPtr 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c35ab13d5cf2448135b1e07405a1e31a5eec86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116668"
---
# <a name="ccomqiptr-class"></a>CComQIPtr 類別

用來管理 COM 介面指標的智慧型指標類別。

## <a name="syntax"></a>語法

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
COM 介面，用來指定要儲存的指標的類型。

*piid*<br/>
指向 IID *T*。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|將指標指派給成員的指標。|

## <a name="remarks"></a>備註

使用 ATL`CComQIPtr`並[CComPtr](../../atl/reference/ccomptr-class.md)若要管理 COM 介面指標，這兩者都衍生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 這兩個類別執行自動參考計數，透過呼叫`AddRef`和`Release`。 多載的運算子處理指標作業。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>需求

**標頭：** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

建構函式。

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>參數

*lp*<br/>
用來初始化介面指標。

*T*<br/>
COM 介面。

*piid*<br/>
指向 IID *T*。

##  <a name="operator_eq"></a>  CComQIPtr::operator =

指派運算子。

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>參數

*lp*<br/>
用來初始化介面指標。

*T*<br/>
COM 介面。

*piid*<br/>
指向 IID *T*。

### <a name="return-value"></a>傳回值

讓指標回到更新`CComQIPtr`物件。

## <a name="see-also"></a>另請參閱

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase 類別](../../atl/reference/ccomptrbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)
