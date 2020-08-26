---
title: IGetDataSourceImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 4c8af66f41724c5a99dfe271a7dd8babc3a993a5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843959"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 類別

提供 [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) 物件的執行。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IGetDataSourceImpl` 。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[GetDataSource](#getdatasource)|傳回建立會話之資料來源物件上的介面指標。|

## <a name="remarks"></a>備註

這是會話上的強制介面，用來取得資料來源物件的介面指標。

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a> IGetDataSourceImpl：： GetDataSource

傳回建立會話之資料來源物件上的介面指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IGetDataSource：： GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) 。

### <a name="remarks"></a>備註

如果您需要存取資料來源物件中的屬性，就很有用。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
