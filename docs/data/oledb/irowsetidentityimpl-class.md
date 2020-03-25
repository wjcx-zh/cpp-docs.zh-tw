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
ms.openlocfilehash: 20f558099c02d7de8a20b3cf631812b44a742a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210401"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 類別

執行 OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))介面，以啟用資料列識別的測試。

## <a name="syntax"></a>語法

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IRowsetIdentityImpl`的類別。

*RowClass*<br/>
`HROW`的儲存體單位。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[IsSameRow](#issamerow)|比較兩個數據列控制碼，以查看它們是否參考相同的資料列。|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a>IRowsetIdentityImpl：： IsSameRow

比較兩個數據列控制碼，以查看它們是否參考相同的資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetIdentity：： IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 。

### <a name="remarks"></a>備註

為了比較資料列控制碼，這個方法會將 `HROW` 控制碼轉換成 `RowClass` 成員，並在指標上呼叫 `memcmp`。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
