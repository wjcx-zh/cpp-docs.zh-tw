---
title: db_column |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35ab2472ac9e46b620ca735d06b23806126871e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879629"
---
# <a name="dbcolumn"></a>db_column
將指定之資料行繫結至資料列中的變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `ordinal`  
 序數資料行數目 (**DBCOLUMNINFO**序數) 或對應至要將資料繫結至資料列集中的欄位的資料行名稱 （ANSI 或 Unicode 字串）。 如果您使用數字，您可以略過連續的序數 (例如： 1、 2、 3、 5)。 如果您使用的 OLE DB 提供者支援名稱包含空格。 例如，您可以使用下列格式之一：  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *dbtype* （選擇性）  
 OLE DB[類型指標](https://msdn.microsoft.com/en-us/library/ms711251.aspx)的資料行項目。  
  
 *有效位數*（選擇性）  
 要用於資料行項目有效位數。 如需詳細資訊，請參閱描述`bPrecision`元素[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *標尺*（選擇性）  
 要用於資料行項目小數位數。 如需詳細資訊，請參閱描述`bScale`元素[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *狀態*（選擇性）  
 成員變數，用來容納此資料行的狀態。 狀態指出資料行值是否為資料值或其他值，例如**NULL**。 可能的值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*。  
  
 *長度*（選擇性）  
 成員變數，用來保存資料行的大小，以位元組為單位。  
  
## <a name="remarks"></a>備註  
 **db_column**將指定的資料表資料行繫結至資料列中的變數。 它用來分隔可以參與 OLE DB 中的成員資料`IAccessor`-基礎繫結。 這個屬性會設定通常使用 OLE DB 取用者巨集來定義資料行對應[BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md)， [END_COLUMN_MAP](../data/oledb/end-column-map.md)，和[COLUMN_ENTRY](../data/oledb/column-entry.md)。 這些操作 OLE DB [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)繫結指定的資料行。 您將標記與每個成員**db_column**屬性會佔用一個項目中的資料行項目表單中的資料行對應。 因此，您呼叫這個屬性會放置資料行對應，也就是命令或資料表類別中。  
  
 使用**db_column**是搭配[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)屬性。  
  
 當取用者屬性提供者會將此屬性套用至類別中時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是為您提供的名稱類別，而編譯器也會建立一種類別稱為*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
 應用程式中，使用這個屬性的範例，請參閱 「 範例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)，和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="example"></a>範例  
 此範例中的資料表繫結資料行**長**資料成員，並指定狀態和長度欄位。  
  
```  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## <a name="example"></a>範例  
 這個範例會將繫結至四個資料行**長**，字元字串、 時間戳記，和**DB_NUMERIC**依此順序的整數。  
  
```  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**， `struct`、 成員、 方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
