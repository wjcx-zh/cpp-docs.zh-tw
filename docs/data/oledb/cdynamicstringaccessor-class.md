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
ms.openlocfilehash: 927ea5ceef9ac74ae3cc1e06a47969b537209002
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838161"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 類別

讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。

## <a name="syntax"></a>語法

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>規格需求

**標頭**： atldbcli.h。h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[GetString](#getstring)|擷取指定資料行的資料做為字串。|
|[SetString](#setstring)|設定指定資料行的資料做為字串。|

## <a name="remarks"></a>備註

雖然 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 會以提供者所報告的原生格式來要求資料，但是 `CDynamicStringAccessor` 提供者會要求提供者從資料存放區中提取所有資料，以做為字串資料。 這特別適用于不需要計算資料存放區中值的簡單工作，例如顯示或列印資料存放區的內容。

資料存放區中資料行資料的原生類型是什麼並不重要，只要提供者可以支援資料轉換即可，它會以字串格式提供資料。 如果提供者不支援從原生資料類型轉換為字串 (不常見)，要求的呼叫將傳回成功值 DB_S_ERRORSOCCURED，而對應資料行的狀態將會以 DBSTATUS_E_CANTCONVERTVALUE 來指出轉換問題。

使用 `CDynamicStringAccessor` 方法來取得資料行資訊。 您可以使用此資料行資訊，在執行時間動態建立存取子。

資料行資訊會儲存在由這個類別所建立和管理的緩衝區中。 使用 [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)從緩衝區取得資料，或使用 [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)將資料儲存到緩衝區。

如需使用動態存取子類別的討論和範例，請參閱 [使用動態](../../data/oledb/using-dynamic-accessors.md)存取子。

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a> CDynamicStringAccessor：： GetString

擷取指定資料行的資料做為字串。

### <a name="syntax"></a>語法

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 0值是指書簽資料行（如果有的話）。

*pColumnName*<br/>
在包含資料行名稱的字元字串指標。

### <a name="return-value"></a>傳回值

從指定的資料行抓取之字串值的指標。 值的類型為 `BaseType` ，其為 **CHAR** 或 **WCHAR** ，取決於是否已定義 _UNICODE。 如果找不到指定的資料行，則傳回 Null。

### <a name="remarks"></a>備註

第二個覆寫表單會採用資料行名稱做為 ANSI 字串。 第三個覆寫表單會將資料行名稱視為 Unicode 字串。

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a> CDynamicStringAccessor：： SetString

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
[in] 資料行編號。 資料行編號的開頭為1。 如果有，則特殊值會參考書簽資料行（如果有的話）。

*pColumnName*<br/>
在包含資料行名稱的字元字串指標。

*data*<br/>
在要寫入指定之資料行的字串資料指標。

### <a name="return-value"></a>傳回值

要設定指定資料行之字串值的指標。 值的類型為 `BaseType` ，其為 **CHAR** 或 **WCHAR** ，取決於是否已定義 _UNICODE。

### <a name="remarks"></a>備註

第二個覆寫表單會採用資料行名稱做為 ANSI 字串，而第三個覆寫表單會將資料行名稱視為 Unicode 字串。

如果 _SECURE_ATL 定義為具有非零值，則如果輸入 *資料* 字串的長度超過所參考資料行的允許長度上限，則會產生執行時間判斷提示失敗。 否則，如果輸入字串的長度超過允許的最大長度，則會予以截斷。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)
