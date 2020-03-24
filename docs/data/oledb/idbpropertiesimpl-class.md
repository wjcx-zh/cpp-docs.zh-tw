---
title: IDBPropertiesImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: f873ec4f4eca434d0eb76df86c0891f1a99c2e2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210700"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 類別

提供 `IDBProperties` 介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IDBPropertiesImpl`的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetProperties](#getproperties)|傳回目前在資料來源物件上設定的資料來源、資料來源資訊和初始化屬性群組中的屬性值，或目前設定于之初始化屬性群組中的屬性值。列舉值.|
|[GetPropertyInfo](#getpropertyinfo)|傳回提供者所支援之所有屬性的相關資訊。|
|[SetProperties](#setproperties)|針對枚舉器，設定資料來源和初始化屬性群組、資料來源物件或初始化屬性群組的屬性。|

## <a name="remarks"></a>備註

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85))是資料來源物件的強制介面，以及枚舉器的選擇性介面。 不過，如果列舉值公開[IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))，它必須公開 `IDBProperties`。 `IDBPropertiesImpl` 使用[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)所定義的靜態函式來執行 `IDBProperties`。

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a>IDBPropertiesImpl：： GetProperties

傳回目前在資料來源物件上設定的資料來源、資料來源資訊和初始化屬性群組中的屬性值，或目前設定于之初始化屬性群組中的屬性值。列舉值.

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IDBProperties：： GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) 。

某些參數會對應至 OLE DB 程式設計*人員的*不同名稱參考參數，如 `IDBProperties::GetProperties`所述：

|OLE DB 範本參數|*OLE DB 程式設計人員的參考*參數|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>備註

如果初始化提供者，這個方法會傳回目前在資料來源物件上設定之 DBPROPSET_DATASOURCE、DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT 屬性群組中的屬性值。 如果未初始化提供者，它只會傳回 DBPROPSET_DBINIT 的群組屬性。

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a>IDBPropertiesImpl：： GetPropertyInfo

傳回資料來源所支援的屬性資訊。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IDBProperties：： GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) 。

某些參數會對應至 OLE DB 程式設計*人員的*不同名稱參考參數，如 `IDBProperties::GetPropertyInfo`所述：

|OLE DB 範本參數|*OLE DB 程式設計人員的參考*參數|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>備註

會使用[IDBInitializeImpl：： m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)來執行此功能。

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a>IDBPropertiesImpl：： SetProperties

針對枚舉器，設定資料來源和初始化屬性群組、資料來源物件或初始化屬性群組的屬性。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IDBProperties：： SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) 。

### <a name="remarks"></a>備註

如果初始化提供者，這個方法會為數據源物件設定 DBPROPSET_DATASOURCE、DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT 屬性群組中的屬性值。 如果未初始化提供者，則只會設定 DBPROPSET_DBINIT 群組屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
