---
title: IOpenRowsetImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446331"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 類別

提供 `IOpenRowset` 介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>參數

*SessionClass*<br/>
衍生自 `IOpenRowsetImpl`的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CreateRowset](#createrowset)|建立資料列集物件。 不是由使用者直接呼叫。|
|[OpenRowset](#openrowset)|開啟並傳回資料列集，其中包含單一基表或索引的所有資料列。 （不在為 ATLDB.H 中。H|

## <a name="remarks"></a>備註

[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))介面是 session 物件的必要參數。 它會開啟並傳回一個資料列集，其中包含單一基表或索引的所有資料列。

## <a name="createrowset"></a>IOpenRowsetImpl：： CreateRowset

建立資料列集物件。 不是由使用者直接呼叫。 請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

### <a name="syntax"></a>語法

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>參數

*RowsetClass*<br/>
範本類別成員，代表使用者的資料列集類別。 通常由 wizard 產生。

*pRowsetObj*<br/>
脫銷資料列集物件的指標。 通常不會使用這個參數，但如果您必須在資料列集上執行更多工做，然後才將它傳遞至 COM 物件，則可以使用此參數。 *PRowsetObj*的存留期是由*ppRowset*所系結。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

## <a name="openrowset"></a>IOpenRowsetImpl：： OpenRowset

開啟並傳回資料列集，其中包含單一基表或索引的所有資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

### <a name="remarks"></a>備註

在為 ATLDB.H 中找不到這個方法。H. 當您建立提供者時，它是由 ATL 物件 Wizard 所建立。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)