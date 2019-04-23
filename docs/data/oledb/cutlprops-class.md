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
- CUtlProps
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
ms.openlocfilehash: 3f1af90bcf454a3651dd8de65bbee7cb6b5960ca
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037616"
---
# <a name="cutlprops-class"></a>CUtlProps 類別

會實作各種不同的 OLE DB 屬性的介面屬性 (例如`IDBProperties`， `IDBProperties`，和`IRowsetInfo`)。

## <a name="syntax"></a>語法

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>參數

*T*<br/>
類別，其中包含`BEGIN_PROPSET_MAP`。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetPropValue](#getpropvalue)|從屬性集合中取得的屬性。|
|[IsValidValue](#isvalidvalue)|用來驗證之前先設定屬性的值。|
|[OnInterfaceRequested](#oninterfacerequested)|取用者物件建立介面上呼叫的方法時，會處理要求選擇性的介面。|
|[OnPropertyChanged](#onpropertychanged)|設定屬性來處理鏈結的屬性之後呼叫。|
|[SetPropValue](#setpropvalue)|在屬性集中設定的屬性。|

## <a name="remarks"></a>備註

此類別大部分是實作細節。

`CUtlProps` 在內部設定屬性中包含兩個成員：[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)並[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。

如需有關在屬性集對應中使用的巨集的詳細資訊，請參閱[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)並[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)。

## <a name="getpropvalue"></a> CUtlProps::GetPropValue

從屬性集合中取得的屬性。

### <a name="syntax"></a>語法

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>參數

*pguidPropSet*<br/>
[in]PropSet GUID。

*dwPropId*<br/>
[in]屬性的索引。

*pvValue*<br/>
[out]包含新的屬性值為 variant 的指標。

### <a name="return-value"></a>傳回值

`Failure` 上失敗，以及如果成功，為 S_OK。

## <a name="isvalidvalue"></a> CUtlProps::IsValidValue

用來驗證之前先設定屬性的值。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
陣列中的索引屬性集;如果只有一個屬性組，則為零。

*pDBProp*<br/>
中的新值與屬性 ID [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構。

### <a name="return-value"></a>傳回值

標準的 HRESULT。 預設的傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您有想要在您要用來設定屬性的值上執行任何驗證常式時，您應該覆寫這個函式。 比方說，您無法將 DBPROP_AUTH_PASSWORD 驗證密碼的資料表，以判斷有效的值。

## <a name="oninterfacerequested"></a> Cutlprops:: Oninterfacerequested

取用者呼叫的方法上其中一個物件建立介面時，會處理要求選擇性的介面。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>參數

*riid*<br/>
[in]要求的介面 IID。 如需詳細資訊，請參閱說明*riid*的參數`ICommand::Execute`中*OLE DB 程式設計人員參考*(中*MDAC SDK*)。

### <a name="remarks"></a>備註

`OnInterfaceRequested` 處理取用者要求選擇性的介面，取用者呼叫的方法上其中一個物件建立介面時 (例如`IDBCreateSession`， `IDBCreateCommand`， `IOpenRowset`，或`ICommand`)。 它會設定為要求的介面對應的 OLE DB 屬性。 例如，如果取用者要求`IID_IRowsetLocate`，`OnInterfaceRequested`設定`DBPROP_IRowsetLocate`介面。 如此一來，則會在資料列集建立期間維護正確的狀態。

當取用者呼叫時，會呼叫這個方法`IOpenRowset::OpenRowset`或`ICommand::Execute`。

如果取用者會開啟物件，並要求選擇性的介面，提供者應該設定為 VARIANT_TRUE 介面相關聯的屬性。 若要允許特定屬性的處理`OnInterfaceRequested`的提供者之前，會呼叫`Execute`呼叫方法。 根據預設，`OnInterfaceRequested`處理下列介面：

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

如果您想要處理其他介面，覆寫此程序函式的資料來源、 工作階段、 命令或資料列集類別中的函式。 覆寫應透過一般的設定/取得屬性介面，以確保，設定屬性也會設定任何鏈結的屬性 (請參閱[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md))。

## <a name="onpropertychanged"></a> Cutlprops:: Onpropertychanged

設定屬性來處理鏈結的屬性之後呼叫。

### <a name="syntax"></a>語法

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>參數

*iCurSet*<br/>
陣列中的索引屬性集;如果只有一個屬性組，則為零。

*pDBProp*<br/>
中的新值與屬性 ID [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))結構。

### <a name="return-value"></a>傳回值

標準的 HRESULT。 預設的傳回值為 S_OK。

### <a name="remarks"></a>備註

如果您想要處理鏈結的屬性，例如書籤或更新其值會相依於另一個屬性的值，您應該覆寫這個函式。

### <a name="example"></a>範例

在此函式中，使用者會取得的屬性識別碼`DBPROP*`參數。 現在，就可以比較針對至鏈結的屬性識別碼。 找到的屬性時，`SetProperties`呼叫現在會設定與其他屬性搭配使用的屬性。 在此情況下，如果其中一個取得`DBPROP_IRowsetLocate`， `DBPROP_LITERALBOOKMARKS`，或`DBPROP_ORDEREDBOOKMARKS`屬性，您可以設定`DBPROP_BOOKMARKS`屬性。

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a> CUtlProps::SetPropValue

在屬性集中設定的屬性。

### <a name="syntax"></a>語法

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>參數

*pguidPropSet*<br/>
[in]PropSet GUID。

*dwPropId*<br/>
[in]屬性的索引。

*pvValue*<br/>
[in]包含新的屬性值為 variant 的指標。

### <a name="return-value"></a>傳回值

`Failure` 上失敗，以及如果成功，為 S_OK。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)