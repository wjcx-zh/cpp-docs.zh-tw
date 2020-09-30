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
ms.openlocfilehash: 1e9e636824ff67ee93587637c0e098e625229c06
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509096"
---
# <a name="cutlprops-class"></a>CUtlProps 類別

針對各種 OLE DB 的屬性 (介面執行屬性，例如、、 `IDBProperties` `IDBProperties` 和 `IRowsetInfo`) 。

## <a name="syntax"></a>語法

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>參數

*T*<br/>
包含的類別 `BEGIN_PROPSET_MAP` 。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[GetPropValue](#getpropvalue)|從屬性集取得屬性。|
|[IsValidValue](#isvalidvalue)|在設定屬性之前用來驗證值。|
|[OnInterfaceRequested](#oninterfacerequested)|當取用者在物件建立介面上呼叫方法時，處理選用介面的要求。|
|[OnPropertyChanged](#onpropertychanged)|設定屬性以處理連結的屬性之後呼叫。|
|[SetPropValue](#setpropvalue)|設定屬性集內的屬性。|

## <a name="remarks"></a>備註

此類別大部分是實作為的詳細資料。

`CUtlProps` 包含兩個在內部設定屬性的成員： [GetPropValue](#getpropvalue) 和 [SetPropValue](#setpropvalue)。

如需屬性集對應中所使用之宏的詳細資訊，請參閱 [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) 和 [END_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#end_propset_map)。

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a> CUtlProps：： GetPropValue

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
擴展Variant 的指標，其中包含新的屬性值。

### <a name="return-value"></a>傳回值

`Failure` 失敗時 S_OK，如果成功則為。

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a> CUtlProps：： IsValidValue

在設定屬性之前用來驗證值。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
屬性集陣列中的索引;如果只有一個屬性集，則為零。

*pDBProp*<br/>
[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構中的屬性識別碼和新值。

### <a name="return-value"></a>傳回值

標準 HRESULT。 預設的傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您想要在要用來設定屬性的值上執行任何驗證常式，則應該覆寫此函式。 例如，您可以針對密碼資料表驗證 DBPROP_AUTH_PASSWORD，以判斷有效的值。

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a> CUtlProps：： OnInterfaceRequested

當取用者在其中一個物件建立介面上呼叫方法時，處理選用介面的要求。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>參數

*riid*<br/>
在所要求介面的 IID。 如需詳細資訊，請參閱*riid* `ICommand::Execute` *MDAC SDK*) 中 OLE DB 程式設計*人員參考* (中的 riid 參數描述。

### <a name="remarks"></a>備註

`OnInterfaceRequested` 當取用者在其中一個物件建立 (介面上呼叫方法時（例如 `IDBCreateSession` 、 `IDBCreateCommand` 、 `IOpenRowset` 或) ），處理選擇性介面的取用者要求 `ICommand` 。 它會為要求的介面設定對應的 OLE DB 屬性。 例如，如果取用者要求 `IID_IRowsetLocate` ，則 `OnInterfaceRequested` 設定 `DBPROP_IRowsetLocate` 介面。 這樣做會在資料列集建立期間維持正確的狀態。

當取用者呼叫或時，會呼叫這個方法 `IOpenRowset::OpenRowset` `ICommand::Execute` 。

如果取用者開啟物件，並要求選擇性的介面，則提供者應該將與該介面相關聯的屬性設定為 VARIANT_TRUE。 若要允許屬性特定的處理， `OnInterfaceRequested` 會在呼叫提供者的方法之前呼叫 `Execute` 。 預設會 `OnInterfaceRequested` 處理下列介面：

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

如果您想要處理其他介面，請在您的資料來源、會話、命令或資料列集類別中覆寫此函數，以處理函式。 您的覆寫應該經過一般 set/get 屬性介面，以確保設定屬性也會設定任何連結的屬性 (請參閱 [OnPropertyChanged](#onpropertychanged)) 。

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a> CUtlProps：： OnPropertyChanged

設定屬性以處理連結的屬性之後呼叫。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
屬性集陣列中的索引;如果只有一個屬性集，則為零。

*pDBProp*<br/>
[DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構中的屬性識別碼和新值。

### <a name="return-value"></a>傳回值

標準 HRESULT。 預設的傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您想要處理連結的屬性，例如其值相依于另一個屬性值的書簽或更新，您應該覆寫此函數。

### <a name="example"></a>範例

在此函數中，使用者從參數取得屬性識別碼 `DBPROP*` 。 現在，您可以將識別碼與屬性進行比較，以進行鏈。 當找到屬性時， `SetProperties` 會使用現在會與其他屬性一起設定的屬性來呼叫。 在此情況下，如果一個取得 `DBPROP_IRowsetLocate` 、 `DBPROP_LITERALBOOKMARKS` 或 `DBPROP_ORDEREDBOOKMARKS` 屬性，就可以設定 `DBPROP_BOOKMARKS` 屬性。

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a> CUtlProps：： SetPropValue

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

`Failure` 失敗時 S_OK，如果成功則為。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
