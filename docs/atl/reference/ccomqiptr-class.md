---
title: CComQIPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327424"
---
# <a name="ccomqiptr-class"></a>CComQIPtr 類別

用於管理 COM 介面指標的智慧指標類。

## <a name="syntax"></a>語法

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
指定要儲存的指標類型的 COM 介面。

*皮伊德*<br/>
指向*T*的 IID 的指標。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComQIPtr:CComQIPtr](#ccomqiptr)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComQIPtr::操作員 |](#operator_eq)|分配指向成員指標的指標。|

## <a name="remarks"></a>備註

ATL`CComQIPtr`使用與[CComPtr](../../atl/reference/ccomptr-class.md)來管理 COM 介面指標,這兩個指標都派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 兩個類都通過調用`AddRef`和`Release`執行自動引用計數。 重載運算符處理指標操作。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr:CComQIPtr

建構函式。

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>參數

*lp*<br/>
用於初始化介面指標。

*T*<br/>
COM 介面。

*皮伊德*<br/>
指向*T*的 IID 的指標。

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::操作員 |

分配運算符。

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>參數

*lp*<br/>
用於初始化介面指標。

*T*<br/>
COM 介面。

*皮伊德*<br/>
指向*T*的 IID 的指標。

### <a name="return-value"></a>傳回值

返回指向更新`CComQIPtr`物件的指標。

## <a name="see-also"></a>另請參閱

[CComPtr:CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr:CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase 類別](../../atl/reference/ccomptrbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComQIPtr 元素類別](../../atl/reference/ccomqiptrelementtraits-class.md)
