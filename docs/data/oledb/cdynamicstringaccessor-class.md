---
title: CDynamicStringAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211859"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 類別

讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。

## <a name="syntax"></a>語法

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetString](#getstring)|擷取指定資料行的資料做為字串。|
|[SetString](#setstring)|設定指定資料行的資料做為字串。|

## <a name="remarks"></a>備註

雖然[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)會以提供者所報告的原生格式來要求資料，`CDynamicStringAccessor` 要求提供者會從資料存放區中提取所有資料，並以字串資料的形式來存取。 這特別適用于不需要計算資料存放區中值的簡單工作，例如顯示或列印資料存放區的內容。

資料存放區中資料行資料的原生類型是什麼並不重要，只要提供者可以支援資料轉換即可，它會以字串格式提供資料。 如果提供者不支援從原生資料類型轉換為字串 (不常見)，要求的呼叫將傳回成功值 DB_S_ERRORSOCCURED，而對應資料行的狀態將會以 DBSTATUS_E_CANTCONVERTVALUE 來指出轉換問題。

使用 `CDynamicStringAccessor` 方法來取得資料行資訊。 您可以使用此資料行資訊，在執行時間動態建立存取子。

資料行資訊會儲存在此類別所建立和管理的緩衝區中。 使用[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)從緩衝區取得資料，或使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)將其儲存到緩衝區。

如需使用動態存取子類別的討論和範例，請參閱[使用動態存取](../../data/oledb/using-dynamic-accessors.md)子。

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor：： GetString

擷取指定資料行的資料做為字串。

### <a name="syntax"></a>語法

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pColumnName*<br/>
在包含資料行名稱之字元字串的指標。

### <a name="return-value"></a>傳回值

從指定的資料行抓取之字串值的指標。 此值的類型 `BaseType`，將會是**CHAR**或**WCHAR** ，視 _UNICODE 是否已定義而定。 如果找不到指定的資料行，則傳回 Null。

### <a name="remarks"></a>備註

第二個覆寫表單會採用資料行名稱做為 ANSI 字串。 第三個覆寫表單會採用資料行名稱做為 Unicode 字串。

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor：： SetString

設定指定資料行的資料做為字串。

### <a name="syntax"></a>語法

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 特殊值0指的是書簽資料行（如果有的話）。

*pColumnName*<br/>
在包含資料行名稱之字元字串的指標。

*data*<br/>
在要寫入指定資料行之字串資料的指標。

### <a name="return-value"></a>傳回值

要設定指定資料行之字串值的指標。 此值的類型 `BaseType`，將會是**CHAR**或**WCHAR** ，視 _UNICODE 是否已定義而定。

### <a name="remarks"></a>備註

第二個覆寫表單會採用資料行名稱作為 ANSI 字串，而第三個覆寫表單會將資料行名稱當做 Unicode 字串。

如果 _SECURE_ATL 定義為具有非零值，則如果輸入*資料*字串長度超過所參考資料行的最大容許長度，就會產生執行時間判斷提示失敗。 否則，如果輸入字串超過允許的最大長度，則會截斷。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)
