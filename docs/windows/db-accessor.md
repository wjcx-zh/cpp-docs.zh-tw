---
title: db_accessor |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 727e67ad5bceb396da98463b77fb75f2f99154b3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650007"
---
# <a name="dbaccessor"></a>db_accessor
群組`db_column`參與屬性`IAccessor`為基礎的繫結。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *num*  
 指定存取子數目 （以零為起始的整數索引）。 您必須指定存取子以遞增的數字順序，使用整數，或定義值。  
  
 *auto*  
 布林值，指定是否自動擷取 (TRUE) 或未擷取 (FALSE) 的存取子。  
  
## <a name="remarks"></a>備註  
 **db_accessor**定義為基礎的 OLE DB 存取子後續`db_column`和`db_param`相同類別或函式內的屬性。 **db_accessor**是可用的成員層級，使用群組`db_column`參與 OLE DB 屬性`IAccessor`-基礎繫結。 搭配使用時使用它`db_table`或`db_command`屬性。 呼叫這個屬性就類似於呼叫[BEGIN_ACCESSOR](../data/oledb/begin-accessor.md)並[END_ACCESSOR](../data/oledb/end-accessor.md)巨集。  
  
 **db_accessor**會產生一個資料列集，並將它繫結至對應的存取子對應。 如果您不能呼叫**db_accessor**存取子 0 將會自動產生，且所有資料行繫結將會對應到這個存取子區塊。  
  
 **db_accessor**群組資料庫資料行繫結到一或多個存取子。 如需情況下，您需要使用多重存取子的討論，請參閱 <<c0> [ 使用的資料列集上的多個存取子](../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另請參閱中的 「 使用者記錄支援的多個存取子 」[使用者記錄](../data/oledb/user-records.md)。  
  
 當取用者的屬性提供者會將此屬性套用至類別時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是您所指定的名稱類別，而編譯器也會建立一個叫做類別*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
## <a name="example"></a>範例  
 下列範例會使用**db_accessor** Orders 資料表中從 Northwind 資料庫的兩個存取子的群組資料行。 存取子 0，自動存取子，並不是存取子為 1。  
  
```cpp  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|屬性區塊|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   