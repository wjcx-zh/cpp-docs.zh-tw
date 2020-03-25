---
title: IRowsetCreatorImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: a53cd653258980d21e9dd297ae61c458732b7250
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210544"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 類別

會執行與 `IObjectWithSite` 相同的功能，但也會啟用 OLE DB 屬性 `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`。

## <a name="syntax"></a>語法

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IRowsetCreator`的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[SetSite](#setsite)|設定包含資料列集物件的網站。|

## <a name="remarks"></a>備註

這個類別繼承自[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) ，並覆寫[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 當提供者命令或會話物件建立資料列集時，它會在尋找 `IObjectWithSite` 的資料列集物件上呼叫 `QueryInterface`，並呼叫 `SetSite` 以網站介面的形式傳遞資料列集物件的 `IUnkown` 介面。

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>IRowsetCreatorImpl：： SetSite

設定包含資料列集物件的網站。 如需詳細資訊，請參閱[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>參數

*pCreator*<br/>
在管理資料列集物件之網站的 `IUnknown` 介面指標的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此外，`IRowsetCreatorImpl::SetSite` 會啟用 OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` 屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
