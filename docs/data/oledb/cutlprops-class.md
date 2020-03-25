---
title: CUtlProps 類別
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 3498ec1250d9443007acb3b12ec25983a71587d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211103"
---
# <a name="cutlprops-class"></a>CUtlProps 類別

會針對各種 OLE DB 屬性介面（例如 `IDBProperties`、`IDBProperties`和 `IRowsetInfo`）來執行屬性。

## <a name="syntax"></a>語法

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>參數

*T*<br/>
包含 `BEGIN_PROPSET_MAP`的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetPropValue](#getpropvalue)|從屬性集取得屬性。|
|[IsValidValue](#isvalidvalue)|在設定屬性之前用來驗證值。|
|[OnInterfaceRequested](#oninterfacerequested)|當取用者在物件建立介面上呼叫方法時，處理選擇性介面的要求。|
|[OnPropertyChanged](#onpropertychanged)|在設定屬性以處理連結的屬性後呼叫。|
|[SetPropValue](#setpropvalue)|設定屬性集內的屬性。|

## <a name="remarks"></a>備註

此類別大多是一個執行詳細資料。

`CUtlProps` 包含在內部設定屬性的兩個成員： [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)和[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。

如需屬性集對應中所用宏的詳細資訊，請參閱[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)和[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)。

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a>CUtlProps：： GetPropValue

從屬性集取得屬性。

### <a name="syntax"></a>語法

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>參數

*pguidPropSet*<br/>
在PropSet 的 GUID。

*dwPropId*<br/>
在屬性索引。

*pvValue*<br/>
脫銷Variant 的指標，其中包含新的屬性值。

### <a name="return-value"></a>傳回值

`Failure` 失敗時，S_OK 成功。

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a>CUtlProps：： IsValidValue

在設定屬性之前用來驗證值。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
屬性集陣列中的索引。如果只有一個屬性集，則為零。

*pDBProp*<br/>
[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構中的屬性識別碼和新值。

### <a name="return-value"></a>傳回值

標準 HRESULT。 預設傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您想要在要用來設定屬性的值上執行任何驗證常式，您應該覆寫此函式。 例如，您可以針對密碼資料表驗證 DBPROP_AUTH_PASSWORD，以判斷有效的值。

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a>CUtlProps：： OnInterfaceRequested

當取用者在其中一個物件建立介面上呼叫方法時，處理選擇性介面的要求。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>參數

*riid*<br/>
在所要求介面的 IID。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*（在*MDAC SDK*中）中 `ICommand::Execute` 的*riid*參數描述。

### <a name="remarks"></a>備註

當取用者在其中一個物件建立介面（例如 `IDBCreateSession`、`IDBCreateCommand`、`IOpenRowset`或 `ICommand`）上呼叫方法時，`OnInterfaceRequested` 會處理選擇性介面的取用者要求。 它會為要求的介面設定對應的 OLE DB 屬性。 例如，如果取用者要求 `IID_IRowsetLocate`，`OnInterfaceRequested` 會設定 `DBPROP_IRowsetLocate` 介面。 這麼做會在資料列集建立期間維持正確的狀態。

當取用者呼叫 `IOpenRowset::OpenRowset` 或 `ICommand::Execute`時，會呼叫這個方法。

如果取用者開啟物件並要求選用的介面，則提供者應該將與該介面相關聯的屬性設定為 VARIANT_TRUE。 若要允許屬性特定的處理，在呼叫提供者的 `Execute` 方法之前，會呼叫 `OnInterfaceRequested`。 根據預設，`OnInterfaceRequested` 會處理下列介面：

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

如果您想要處理其他介面，請覆寫資料來源、會話、命令或資料列集類別中的這個函式，以處理函式。 您的覆寫應經過一般設定/取得屬性介面，以確保設定屬性也會設定任何連結的屬性（請參閱[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)）。

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a>CUtlProps：： OnPropertyChanged

在設定屬性以處理連結的屬性後呼叫。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
屬性集陣列中的索引。如果只有一個屬性集，則為零。

*pDBProp*<br/>
[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構中的屬性識別碼和新值。

### <a name="return-value"></a>傳回值

標準 HRESULT。 預設傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您想要處理連結的屬性（例如，其值相依于另一個屬性值的書簽或更新），您應該覆寫此函數。

### <a name="example"></a>範例

在此函數中，使用者會從 `DBPROP*` 參數取得屬性識別碼。 現在，您可以將識別碼與屬性相比較，以進行連鎖。 找到屬性時，會使用屬性來呼叫 `SetProperties`，此屬性現在會與另一個屬性一起設定。 在此情況下，如果其中一個取得 `DBPROP_IRowsetLocate`、`DBPROP_LITERALBOOKMARKS`或 `DBPROP_ORDEREDBOOKMARKS` 屬性，則可以設定 `DBPROP_BOOKMARKS` 屬性。

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a>CUtlProps：： SetPropValue

設定屬性集內的屬性。

### <a name="syntax"></a>語法

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>參數

*pguidPropSet*<br/>
在PropSet 的 GUID。

*dwPropId*<br/>
在屬性索引。

*pvValue*<br/>
在Variant 的指標，其中包含新的屬性值。

### <a name="return-value"></a>傳回值

`Failure` 失敗時，S_OK 成功。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
