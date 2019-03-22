---
title: db_param （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 2de051b099da5f179a7634cddfb359d85f4b1f83
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328788"
---
# <a name="dbparam"></a>db_param

關聯的輸入或輸出參數中指定的成員變數，並分隔的變數。

## <a name="syntax"></a>語法

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>參數

*ordinal*<br/>
中要將資料繫結至資料列集的欄位對應的資料行號碼 （DBCOLUMNINFO 序數）。

*paramtype*<br/>
（選擇性）若要設定的參數類型。 提供者支援只有參數 I/O 類型所支援的基礎資料來源。 類型是一或多個 DBPARAMIOENUM 值的組合：

- DBPARAMIO_INPUT 輸入參數。

- DBPARAMIO_OUTPUT 輸出參數。

- DBPARAMIO_NOTPARAM 存取子沒有任何參數。 設定`eParamIO`為此值在資料列存取子會提醒使用者參數被忽略。

*dbtype*<br/>
（選擇性）OLE DB[型別指示器](/previous-versions/windows/desktop/ms711251(v=vs.85))的資料行項目。

*precision*<br/>
（選擇性）要用於資料行項目有效位數。 如需詳細資訊，請參閱說明`bPrecision`項目[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))

*scale*<br/>
（選擇性）要用於資料行項目小數位數。 如需詳細資訊，請參閱說明`bScale`項目[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))

*status*<br/>
（選擇性）成員變數，用來保存此資料行的狀態。 狀態會指出資料行的值是資料值或其他值，例如 NULL。 如需可能的值，請參閱[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))中*OLE DB 程式設計人員參考*。

*length*<br/>
（選擇性）成員變數，用來保存資料行的大小，以位元組為單位。

## <a name="remarks"></a>備註

**db_param**定義的參數，您在命令中使用，因此使用它來搭配`db_command`。 例如，您可以使用**db_param**繫結中的 SQL 查詢或預存程序的參數。 由問號 （？），表示參數的預存程序中，您應該將資料成員繫結參數會出現的順序。

**db_param**分隔可以參與 OLE DB 中的成員資料`ICommandWithParameters`為基礎的繫結。 它會設定參數類型 （輸入或輸出）、 OLE DB 類型、 有效位數、 小數位數、 狀態和長度為指定的參數。 此屬性會插入的 OLE DB 取用者巨集 BEGIN_PARAM_MAP...END_PARAM_MAP. 您將標記與每個成員**db_param**屬性會佔用 COLUMN_ENTRY 形式對應中的一個項目。

**db_param**搭配使用[db_table](db-table.md)或是[db_command](db-command.md)屬性。

當取用者的屬性提供者會將此屬性套用至類別時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是您所指定的名稱類別，而編譯器也會建立一個叫做類別*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

## <a name="example"></a>範例

下列範例會建立根據 Northwind 資料庫中的 SalesbyYear 預存程序的命令類別。 會將關聯的預存程序的第一個參數`m_RETURN_VALUE`變數，並將其定義為 output 參數。 （輸入） 的最後兩個參數，與將建立關聯`m_Beginning_Date`和`m_Ending_Date`。

下列範例會關聯`nOutput`變數以輸出參數。

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
|**適用於**|**類別**， **struct**、 member、 method、 local|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](ole-db-consumer-attributes.md)
