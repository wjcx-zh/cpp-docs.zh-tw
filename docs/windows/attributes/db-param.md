---
title: db_param （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 1a32dcceae1e4e4fbc730101381eda84b5350ffd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215305"
---
# <a name="db_param"></a>db_param

將指定的成員變數與輸入或輸出參數產生關聯，並分隔變數。

## <a name="syntax"></a>語法

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>參數

*序數*<br/>
對應至資料列集中之欄位的欄號（DBCOLUMNINFO 序數），用來系結資料。

*paramtype*<br/>
選擇性要為參數設定的類型。 提供者只支援基礎資料來源所支援的參數 i/o 類型。 類型是一或多個 DBPARAMIOENUM 值的組合：

- DBPARAMIO_INPUT ：輸入參數。

- DBPARAMIO_OUTPUT ：輸出參數。

- DBPARAMIO_NOTPARAM ：存取子沒有參數。 `eParamIO`在資料列存取子中設定此值，會提醒使用者參數被忽略。

*dbtype*<br/>
選擇性資料行專案的 OLE DB[類型指標](/previous-versions/windows/desktop/ms711251(v=vs.85))。

*有效位數*<br/>
選擇性要用於資料行專案的有效位數。 如需詳細資訊，請參閱 `bPrecision` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素描述

*scale*<br/>
選擇性要用於資料行專案的尺規。 如需詳細資訊，請參閱 `bScale` [DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素描述

*status*<br/>
選擇性用來保存此資料行之狀態的成員變數。 狀態會指出資料行值是否為數據值或其他值，例如 Null。 如需可能的值，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))。

*length*<br/>
選擇性用來保存資料行大小的成員變數（以位元組為單位）。

## <a name="remarks"></a>備註

**db_param**會定義您在命令中使用的參數;因此，您可以將它與搭配使用 `db_command` 。 例如，您可以使用**db_param**來系結 SQL 查詢或預存程式中的參數。 預存程式中的參數是以問號（？）表示，您應該以參數出現的順序來系結資料成員。

**db_param**分隔可以參與 OLE DB 型系結的成員資料 `ICommandWithParameters` 。 它會為指定的參數設定參數類型（輸入或輸出）、OLE DB 類型、有效位數、小數位數、狀態和長度。 這個屬性會將 OLE DB 取用者宏 BEGIN_PARAM_MAP .。。END_PARAM_MAP。 您以**db_param**屬性標記的每個成員，都會以 COLUMN_ENTRY 的形式在地圖中佔用一個專案。

**db_param**會搭配[db_table](db-table.md)或[db_command](db-command.md)屬性一起使用。

當取用者屬性提供者將此屬性套用至類別時，編譯器會將類別重新命名為 \_ *YourClassName*存取子，其中*YourClassName*是您為類別提供的名稱，而編譯器也會建立名為*YourClassName*的類別，其衍生自 \_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會根據 Northwind 資料庫中的 SalesbyYear 預存程式來建立 command 類別。 它會將預存程式中的第一個參數與變數產生關聯 `m_RETURN_VALUE` ，並將它定義為 output 參數。 它會將最後兩個（輸入）參數與和產生關聯 `m_Beginning_Date` `m_Ending_Date` 。

下列範例會將 `nOutput` 變數與輸出參數產生關聯。

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`class`**、 **`struct`** 、member、method、local|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 取用者屬性](ole-db-consumer-attributes.md)
