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
ms.openlocfilehash: 85fddb9b77cfc089b2236f2ff82944fec6ef9632
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036097"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 類別

可讓您存取資料來源做為字串資料，就不會知道的資料存放區的結構描述 （基礎結構）。

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
|[GetXMLColumnData](#getxmlcolumndata)|擷取的資料行資訊。|
|[GetXMLRowData](#getxmlrowdata)|資料列所擷取資料表的整個的內容。|

## <a name="remarks"></a>備註

不過，`CXMLAccessor`不同於`CDynamicStringAccessorW`，因為它會將轉換從資料存放區做為 XML 格式 （標記） 的資料存取的所有資料。 這是特別適用於 XML 感知的 Web 網頁的輸出。 XML 標記名稱將會儘可能密集地符合資料存放區的資料行名稱。

使用`CDynamicAccessor`方法來取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。

資料行資訊會儲存在緩衝區中由這個類別建立和管理。 取得資料行資訊使用[GetXMLColumnData](#getxmlcolumndata) ，或取得資料行資料所使用的資料列[GetXMLRowData](#getxmlrowdata)。

## <a name="example"></a>範例

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> CXMLAccessor::GetXMLColumnData

依資料行中擷取為 XML 格式的字串資料，資料表的資料行型別資訊。

### <a name="syntax"></a>語法

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>參數

*strOutput*<br/>
[out]包含要擷取的資料行型別資訊的字串緩衝區的參考。 字串格式化與資料存放區的資料行名稱相符的 XML 標記名稱。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

下面顯示如何在 XML 中格式化的資料行型別資訊。 `type` 指定資料行的資料類型。 請注意，資料類型基礎 OLE DB 資料類型，不是其中一個所存取的資料庫。

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> CXMLAccessor::GetXMLRowData

擷取為 XML 格式的字串資料的資料表的整個內容，依資料列。

### <a name="syntax"></a>語法

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>參數

*strOutput*<br/>
[out]包含要擷取的資料表資料之緩衝區的參考。 資料會格式化為字串資料的資料存放區的資料行名稱相符的 XML 標記名稱。

*bAppend*<br/>
[in]布林值，指定是否要將字串附加至輸出資料的結尾。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

下面顯示如何在 XML 中格式化資料列資料。 `DATA` 以下呈現的資料列資料。 使用 move 方法移至所需的資料列。

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)