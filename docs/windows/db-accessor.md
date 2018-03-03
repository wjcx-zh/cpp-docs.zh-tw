---
title: "db_accessor |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5faa84773fbf1fe15fd0223c97f0361f1215b149
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dbaccessor"></a>db_accessor
群組**db_column**參與屬性`IAccessor`-基礎繫結。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *num*  
 指定存取子數目 （以零為起始的整數索引）。 您必須指定存取子是以遞增的數字順序，使用整數或定義值。  
  
 *auto*  
 布林值，指定是否自動擷取存取子 (**TRUE**) 或未擷取 (**FALSE**)。  
  
## <a name="remarks"></a>備註  
 **db_accessor**定義為基礎的 OLE DB 存取子後續**db_column**和**db_param**相同類別或函式中的屬性。 **db_accessor**在成員層級可供使用，而且是群組**db_column**參與 OLE DB 屬性`IAccessor`-基礎繫結。 使用其中一種一起**db_table**或**db_command**屬性。 呼叫這個屬性是類似於呼叫[BEGIN_ACCESSOR](../data/oledb/begin-accessor.md)和[END_ACCESSOR](../data/oledb/end-accessor.md)巨集。  
  
 **db_accessor**會產生資料列集，並將它繫結至對應的存取子對應。 如果您不會呼叫**db_accessor**存取子 0 將會自動產生，且所有資料行繫結將會對應到此存取子區塊。  
  
 **db_accessor**群組資料庫資料行繫結到一或多個存取子。 如需您要使用多重存取子的案例的討論，請參閱[資料列集上使用多重存取子](../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另請參閱中的 「 使用者記錄支援的多個存取子 」[使用者資料錄](../data/oledb/user-records.md)。  
  
 當取用者屬性提供者會將此屬性套用至類別中時，編譯器會重新命名的類別\_ *YourClassName*存取子，其中*YourClassName*是為您提供的名稱類別，而編譯器也會建立一種類別稱為*YourClassName*，其衍生自\_ *YourClassName*存取子。  在 [類別] 檢視中，您會看到這兩個類別。  
  
## <a name="example"></a>範例  
 下列範例會使用**db_accessor** Orders 資料表中兩個存取子到 Northwind 資料庫中的群組資料行。 存取子 0 是自動存取子，並存取子 1 不是。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)   
