---
title: IRowsetIdentityImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 48ed687ff67208109b5a2acf400d98491b4c769a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836139"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 類別

會執行 OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) 介面，以啟用資料列識別的測試。

## <a name="syntax"></a>語法

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IRowsetIdentityImpl` 。

*RowClass*<br/>
的儲存單位 `HROW` 。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[IsSameRow](#issamerow)|比較兩個數據列控制碼，看看它們是否參考相同的資料列。|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a> IRowsetIdentityImpl：： IsSameRow

比較兩個數據列控制碼，看看它們是否參考相同的資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetIdentity：： IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 。

### <a name="remarks"></a>備註

為了比較資料列控制碼，這個方法會將 `HROW` 控制碼轉換成 `RowClass` 成員和指標的呼叫 `memcmp` 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
