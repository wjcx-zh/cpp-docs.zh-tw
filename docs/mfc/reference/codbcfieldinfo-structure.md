---
title: "CODBCFieldInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODBCFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CODBCFieldInfo 結構"
  - "ODBC, 資料來源資訊"
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CODBCFieldInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CODBCFieldInfo` 結構在 ODBC 資料來源包含欄位的資訊。  
  
## 語法  
  
```  
  
      struct CODBCFieldInfo  
{  
   CString m_strName;  
   SWORD m_nSQLType;  
   UDWORD m_nPrecision;  
   SWORD m_nScale;  
   SWORD m_nNullability;  
};  
```  
  
#### 參數  
 `m_strName`  
 欄位名稱。  
  
 *m\_nSQLType*  
 SQL資料型別的欄位。  這可以是 ODBC SQL 資料型別或驅動程式特定 SQL 資料型別。  如需有效 ODBC SQL 資料型別清單，請參閱「 SQL 資料型別」在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  如需驅動程式特定 SQL 資料型別的詳細資訊，請參閱驅動程式的資料。  
  
 *m\_nPrecision*  
 欄位的最大精確度。  如需詳細資訊，請參閱、精確度、小數點位數、長度和顯示大小」在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m\_nScale*  
 縮放欄位。  如需詳細資訊，請參閱、精確度、小數點位數、長度和顯示大小」在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m\_nNullability*  
 欄位是否接受 null 值。  這可以是兩個值之一: **SQL\_NULLABLE** ，如果欄位接受 null 值或 **SQL\_NO\_NULLS** ，如果欄位不接受 null 值。  
  
## 備註  
 若要擷取這項資訊，請呼叫 [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)。  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)