---
title: CDynamicStringAccessor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 178308fc777d5d1c38bbe0ace586bdb6855a7863
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063116"
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

雖然[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)要求提供者，報告的原生格式資料`CDynamicStringAccessor`要求提供者擷取從資料存放區做為字串資料存取的所有資料。 這是特別適合用於簡單的工作不需要計算值的資料存放區，例如顯示或列印的資料存放區的內容。

資料存放區中資料行資料的原生類型是什麼並不重要，只要提供者可以支援資料轉換即可，它會以字串格式提供資料。 如果提供者不支援從原生資料類型轉換為字串 （這是不常見），要求的呼叫會傳回成功值 DB_S_ERRORSOCCURED，和對應的資料行的狀態會指出轉換問題DBSTATUS_E_CANTCONVERTVALUE。

使用`CDynamicStringAccessor`方法來取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。

資料行資訊會儲存在緩衝區中由這個類別建立和管理。 取得從緩衝區使用的資料[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)，或將它儲存至緩衝區使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)。

討論和使用動態存取子類別的範例，請參閱[使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。

## <a name="getstring"></a> Cdynamicstringaccessor:: Getstring

擷取指定資料行的資料做為字串。

### <a name="syntax"></a>語法

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。

*pColumnName*<br/>
[in]包含資料行名稱的字元字串指標。

### <a name="return-value"></a>傳回值

從指定的資料行中擷取的字串值的指標。 值為類型`BaseType`，這將成為**CHAR**或**WCHAR**根據 _UNICODE 是否已定義。 如果找不到指定的資料行，則傳回 NULL。

### <a name="remarks"></a>備註

第二個覆寫表單會採用資料行名稱做為 ANSI 字串。 第三個覆寫表單會採用資料行名稱為 Unicode 字串。

## <a name="setstring"></a> Cdynamicstringaccessor:: Setstring

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
[in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，特殊的值為 0 就是指書籤資料行。

*pColumnName*<br/>
[in]包含資料行名稱的字元字串指標。

*data*<br/>
[in]要寫入至指定的資料行的字串資料指標。

### <a name="return-value"></a>傳回值

要用來設定指定的資料行的字串值指標。 值為類型`BaseType`，這將成為**CHAR**或**WCHAR**根據 _UNICODE 是否已定義。

### <a name="remarks"></a>備註

第二個覆寫表單會為 ANSI 字串的資料行名稱和第三個覆寫表單會採用 Unicode 字串資料行名稱。

如果執行階段判斷提示失敗如果 _SECURE_ATL 定義為具有非零值，就會產生輸入*資料*字串的長度超過允許長度上限的參考的資料行。 否則輸入的字串會被截斷，如果名稱長度超過允許長度上限。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)