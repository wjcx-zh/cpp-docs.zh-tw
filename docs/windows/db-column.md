---
title: db_column |Microsoft Docs
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
ms.openlocfilehash: 10acf2b69eaa6b49145e671d437f18dfaff8e499
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195786"
---
# <a name="dbcolumn"></a>db_column

將指定的資料行繫結至資料列中的變數。

## <a name="syntax"></a>語法

```cpp
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

*序數*  
序數資料行編號 (`DBCOLUMNINFO`序數) 或要將資料繫結至資料列集中的欄位相對應的資料行名稱 （ANSI 或 Unicode 字串）。 如果您使用數字時，您可以略過連續的序數 (例如： 1、 2、 3、 5)。 如果您使用的 OLE DB 提供者支援它的名稱包含空格。 例如，您可以使用下列格式之一：

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype* （選擇性）  
OLE DB[型別指示器](/previous-versions/windows/desktop/ms711251\(v=vs.85\))的資料行項目。

*有效位數*（選擇性）  
要用於資料行項目有效位數。 如需詳細資訊，請參閱說明`bPrecision`項目[DBBINDING 結構](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*擴展*（選擇性）  
要用於資料行項目小數位數。 如需詳細資訊，請參閱說明`bScale`項目[DBBINDING 結構](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*狀態*（選擇性）  
成員變數，用來保存此資料行的狀態。 狀態會指出資料行的值是資料值或其他值，例如 NULL。 如需可能的值，請參閱[狀態](/previous-versions/windows/desktop/ms722617\(v=vs.85\))中*OLE DB 程式設計人員參考*。

*長度*（選擇性）  
成員變數，用來保存資料行的大小，以位元組為單位。

## <a name="remarks"></a>備註

**db_column**將指定的資料表資料行繫結至資料列中的變數。 它會分隔可以參與 OLE DB 中的成員資料`IAccessor`為基礎的繫結。 這個屬性會設定通常使用的 OLE DB 取用者巨集來定義資料行對應[BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md)， [END_COLUMN_MAP](../data/oledb/end-column-map.md)，並[COLUMN_ENTRY](../data/oledb/column-entry.md)。 這些操作 OLE DB [DBBINDING 結構](/previous-versions/windows/desktop/ms716845\(v=vs.85\))繫結指定的資料行。 您將標記與每個成員**db_column**屬性會佔用的資料行項目表單中的資料行對應中的一個項目。 因此，您呼叫這個屬性會放置資料行對應，也就是命令或資料表類別中。

使用**db_column**是搭配[db_table](../windows/db-table.md)或是[db_command](../windows/db-command.md)屬性。

當取用者的屬性提供者會將此屬性套用至類別時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是您所指定的名稱類別，而編譯器也會建立一個叫做類別*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。

關於應用程式中，使用這個屬性的範例，請參閱 「 範例[AtlAgent](https://github.com/Microsoft/VCSamples)，並[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="example"></a>範例

此範例會將繫結資料行在資料表中**長**資料成員和指定狀態和長度的欄位。

```cpp
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

此範例會將繫結至四個資料行**長**，為字元字串、 時間戳記，以及`DB_NUMERIC`依此順序的整數。

```cpp
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
|**適用於**|**類別**， **struct**、 成員、 方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
