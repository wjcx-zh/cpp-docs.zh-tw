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
ms.openlocfilehash: a3c94c75db21218aae1205bf9c5c379ab772a7f8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843712"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 類別

提供介面的實作為 `IOpenRowset` 。

## <a name="syntax"></a>語法

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>參數

*SessionClass*<br/>
衍生自的類別 `IOpenRowsetImpl` 。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[CreateRowset](#createrowset)|建立資料列集物件。 未直接由使用者呼叫。|
|[[OpenRowset]](#openrowset)|開啟並傳回資料列集，其中包含單一基表或索引的所有資料列。  (不在 ATLDB.H 中。H) |

## <a name="remarks"></a>備註

[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))介面是會話物件的必要項。 它會開啟並傳回資料列集，其中包含單一基表或索引的所有資料列。

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a> IOpenRowsetImpl：： CreateRowset

建立資料列集物件。 未直接由使用者呼叫。 請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

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
代表使用者之資料列集類別的範本類別成員。 通常由 wizard 產生。

*pRowsetObj*<br/>
擴展資料列集物件的指標。 通常不會使用此參數，但如果您必須在資料列集上執行更多工作，才能將它傳遞給 COM 物件，則可以使用此參數。 *PRowsetObj*的存留期是由 *>pprowset*所系結。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a> IOpenRowsetImpl：： OpenRowset

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

在 ATLDB.H 中找不到這個方法。H。 當您建立提供者時，它是由 ATL 物件 Wizard 所建立。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
