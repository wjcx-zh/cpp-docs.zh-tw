---
title: db_param |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7cf5c8e92e7fd6e6e10d7bef0519b1ced4cf62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880682"
---
# <a name="dbparam"></a>db_param
關聯的輸入或輸出參數中指定的成員變數，分隔的變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `ordinal`  
 資料行數目 (**DBCOLUMNINFO**序數) 對應至要將資料繫結至資料列集中的欄位。  
  
 *paramtype* （選擇性）  
 要設定參數的類型。 提供者只支援參數 I/O 類型所支援的基礎資料來源。 型別是一或多個組合**DBPARAMIOENUM**值：  
  
-   **DBPARAMIO_INPUT** ：輸入參數。  
  
-   **DBPARAMIO_OUTPUT** ：輸出參數。  
  
-   **DBPARAMIO_NOTPARAM** ：存取子沒有參數。 設定**eParamIO**這個值以資料列存取子會提醒使用者參數被忽略。  
  
 *dbtype* （選擇性）  
 OLE DB[類型指標](https://msdn.microsoft.com/en-us/library/ms711251.aspx)的資料行項目。  
  
 *有效位數*（選擇性）  
 要用於資料行項目有效位數。 如需詳細資訊，請參閱描述**bPrecision**元素[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *標尺*（選擇性）  
 要用於資料行項目小數位數。 如需詳細資訊，請參閱描述**bScale**元素[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *狀態*（選擇性）  
 成員變數，用來容納此資料行的狀態。 狀態指出資料行值是否為資料值或其他值，例如**NULL**。 可能的值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*。  
  
 *長度*（選擇性）  
 成員變數，用來保存資料行的大小，以位元組為單位。  
  
## <a name="remarks"></a>備註  
 **db_param**定義參數，您在命令中使用，因此使用它與**db_command**。 例如，您可以使用**db_param**繫結中的 SQL 查詢或預存程序的參數。 以問號 （？），代表預存程序中的參數，您應該將資料成員繫結的參數會出現的順序。  
  
 **db_param**分隔可以參與 OLE DB 中的成員資料`ICommandWithParameters`-基礎繫結。 它會設定參數類型 （輸入或輸出）、 OLE DB 類型、 有效位數、 小數位數、 狀態和長度為指定的參數。 這個屬性會插入 OLE DB 取用者巨集 BEGIN_PARAM_MAP...END_PARAM_MAP。 您將標記與每個成員**db_param**屬性會佔用 COLUMN_ENTRY 表單中的對應中的一個項目。  
  
 **db_param**搭配使用其中一種[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)屬性。  
  
 當取用者屬性提供者會將此屬性套用至類別中時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是為您提供的名稱類別，而編譯器也會建立一種類別稱為*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
## <a name="example"></a>範例  
 下列範例會建立 Northwind 資料庫中的 SalesbyYear 預存程序為基礎的命令類別。 它產生關聯的預存程序的第一個參數`m_RETURN_VALUE`變數，並將其定義為 output 參數。 它產生關聯的 （輸入） 的最後兩個參數，與`m_Beginning_Date`和`m_Ending_Date`。  
  
 下列範例將`nOutput`變數以輸出參數。  
  
```  
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
|**適用於**|**class**、 `struct`、member、method、local|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   
