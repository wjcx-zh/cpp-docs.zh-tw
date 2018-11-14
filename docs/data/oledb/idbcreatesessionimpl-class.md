---
title: IDBCreateSessionImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: ecc06bf5e3514ea87c86de17dbafd59b9da9f8b6
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556418"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 類別

提供實作[IDBCreateSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms724076(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自

*SessionClass*<br/>
工作階段物件。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[CreateSession](#createsession)|從資料來源物件建立新的工作階段，並傳回新建立的工作階段上的要求的介面。|

## <a name="remarks"></a>備註

在 資料來源物件上的強制介面。

## <a name="createsession"></a> Idbcreatesessionimpl:: Createsession

從資料來源物件建立新的工作階段，並傳回新建立的工作階段上的要求的介面。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>參數

請參閱[idbcreatesession:: Createsession](https://docs.microsoft.com/previous-versions/windows/desktop/ms714942(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)