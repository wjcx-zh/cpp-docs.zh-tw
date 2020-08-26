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
ms.openlocfilehash: aeeca008499ca43cdcebd008390e5cb6c5a9e63c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845519"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 類別

提供 [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) 介面的實作為。

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
會話物件。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[CreateSession](#createsession)|從資料來源物件建立新的會話，並在新建立的會話上傳回所要求的介面。|

## <a name="remarks"></a>備註

資料來源物件上的強制介面。

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a> IDBCreateSessionImpl：： CreateSession

從資料來源物件建立新的會話，並在新建立的會話上傳回所要求的介面。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IDBCreateSession：： CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
