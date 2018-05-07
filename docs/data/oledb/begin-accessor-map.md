---
title: BEGIN_ACCESSOR_MAP |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR_MAP macro
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e03e4aed105a488d646921fd458496d8d5a950f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="beginaccessormap"></a>BEGIN_ACCESSOR_MAP
標記存取子對應項目的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
BEGIN_ACCESSOR_MAP(x, num)  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 [in] 使用者資料錄類別的名稱。  
  
 *num*  
 [in] 此存取子對應中的存取子數目。  
  
## <a name="remarks"></a>備註  
 如果資料列集上有多個存取子，您必須在開頭指定 `BEGIN_ACCESSOR_MAP` ，並針對每個個別存取子使用 `BEGIN_ACCESSOR` 巨集。 `BEGIN_ACCESSOR` 巨集會以 `END_ACCESSOR` 巨集完成。 存取子對應會以 `END_ACCESSOR_MAP` 巨集完成。  
  
 如果使用者資料錄中只有一個存取子，請使用巨集 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。  
  
## <a name="example"></a>範例  

 ```cpp  
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
 ```

  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)