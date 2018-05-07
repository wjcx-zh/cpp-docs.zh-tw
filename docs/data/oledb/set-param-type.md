---
title: SET_PARAM_TYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SET_PARAM_TYPE
dev_langs:
- C++
helpviewer_keywords:
- SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ab4884032425f13c2cc506d6e66c955eb439f7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
指定 `COLUMN_ENTRY` 巨集輸入、輸出或輸入/輸出之後的 `SET_PARAM_TYPE` 巨集。  
  
## <a name="syntax"></a>語法  
  
```cpp
SET_PARAM_TYPE(type)  
  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 [in] 用來設定參數的類型。  
  
## <a name="remarks"></a>備註  
 提供者只支援基礎資料來源支援的參數輸入/輸出類型。 此類型是一或多個 **DBPARAMIO** 值的組合 (請參閱 [＜OLE DB 程式設計人員參考＞](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 中的 *DBBINDING Structures*(DBBINDING 結構))：  
  
-   **DBPARAMIO_NOTPARAM** ：存取子沒有參數。 通常會在資料列存取子將 **eParamIO** 設定為此值，以提醒使用者參數被忽略。  
  
-   **DBPARAMIO_INPUT** ：輸入參數。  
  
-   **DBPARAMIO_OUTPUT** ：輸出參數。  
  
-   **DBPARAMIO_INPUT &#124; DBPARAMIO_OUTPUT**參數是輸入和輸出參數。  
  
## <a name="example"></a>範例  
```
cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

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

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)