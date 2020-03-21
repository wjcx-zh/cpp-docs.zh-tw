---
title: IRowsetInfoImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: 691871bfc4a9e63167611a3228807fb12e32d1cb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077874"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 類別

提供[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IRowsetInfoImpl`的類別。

*PropClass*<br/>
使用者可定義的屬性類別，預設為*T*。

## <a name="requirements"></a>需求

**標頭：** altdb。h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetProperties](#getproperties)|傳回資料列集 (Rowset) 支援之所有屬性的目前設定。|
|[GetReferencedRowset](#getreferencedrowset)|將介面指標傳回至要套用書簽的資料列集。|
|[GetSpecification](#getspecification)|傳回建立此資料列集之物件 (命令或工作階段) 上的介面指標。|

## <a name="remarks"></a>備註

資料列集上的強制介面。 這個類別會使用在命令類別中定義的[屬性集對應](../../data/oledb/begin-propset-map.md)來實作為資料列集屬性。 雖然資料列集類別似乎是使用命令類別的屬性集，但當資料列集是由命令或會話物件所建立時，它會隨附其本身的執行時間屬性複本。

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a>IRowsetInfoImpl：： GetProperties

傳回 `DBPROPSET_ROWSET` 群組中屬性的目前設定。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetInfo：： GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) 。

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a>IRowsetInfoImpl：： GetReferencedRowset

將介面指標傳回至要套用書簽的資料列集。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetInfo：： GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) 。 *IOrdinal*參數必須是書簽資料行。

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a>IRowsetInfoImpl：： GetSpecification

傳回建立此資料列集之物件 (命令或工作階段) 上的介面指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetInfo：： GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) 。

### <a name="remarks"></a>備註

使用此方法搭配[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) ，從資料來源物件中抓取屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)