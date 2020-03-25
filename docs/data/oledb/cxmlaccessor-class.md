---
title: CXMLAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211038"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 類別

當您不知道資料存放區的架構（基礎結構）時，可讓您以字串資料的形式存取資料來源。

## <a name="syntax"></a>語法

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|抓取資料行資訊。|
|[GetXMLRowData](#getxmlrowdata)|依資料列抓取資料表的整個內容。|

## <a name="remarks"></a>備註

不過，`CXMLAccessor` 不同于 `CDynamicStringAccessorW`，它會將從資料存放區存取的所有資料轉換為 XML 格式（已標記）的資料。 這特別適用于輸出至 XML 感知的網頁。 XML 標記名稱會盡可能符合資料存放區的資料行名稱。

使用 `CDynamicAccessor` 方法來取得資料行資訊。 您可以使用此資料行資訊，在執行時間動態建立存取子。

資料行資訊會儲存在此類別所建立和管理的緩衝區中。 使用[GetXMLColumnData](#getxmlcolumndata)取得資料行資訊，或使用[GetXMLRowData](#getxmlrowdata)依資料列取得資料行資料。

## <a name="example"></a>範例

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor：： GetXMLColumnData

依資料行，將資料表的資料行類型資訊當做 XML 格式的字串資料來抓取。

### <a name="syntax"></a>語法

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>參數

*strOutput*<br/>
脫銷字串緩衝區的參考，其中包含要抓取的資料行類型資訊。 字串會使用符合資料存放區之資料行名稱的 XML 標記名稱進行格式化。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

以下顯示如何在 XML 中格式化資料行類型資訊。 `type` 指定資料行的資料類型。 請注意，資料類型是以 OLE DB 資料類型為基礎，而不是要存取的資料庫。

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor：： GetXMLRowData

依資料列，將資料表的整個內容當做 XML 格式的字串資料來抓取。

### <a name="syntax"></a>語法

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>參數

*strOutput*<br/>
脫銷包含要抓取的資料表資料之緩衝區的參考。 資料會格式化為字串資料，其 XML 標記名稱符合資料存放區的資料行名稱。

*bAppend*<br/>
在布林值，指定是否要在輸出資料的結尾附加字串。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

以下顯示如何在 XML 中格式化資料列資料。 以下 `DATA` 代表資料列資料。 使用 move 方法移至所需的資料列。

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)
