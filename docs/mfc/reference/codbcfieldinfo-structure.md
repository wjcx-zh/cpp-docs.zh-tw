---
title: "CODBCFieldInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC, data source information
- CODBCFieldInfo structure
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1080eb323c599014d84acab94aee4622795fdb96
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo 結構
`CODBCFieldInfo`結構包含在 ODBC 資料來源中欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 欄位的名稱。  
  
 *m_nSQLType*  
 SQL 資料類型的欄位。 這可以是 ODBC SQL 資料型別或驅動程式專屬的 SQL 資料型別。 有效的 ODBC SQL 資料類型的清單，請參閱 「 SQL 資料類型 」，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需驅動程式特定 SQL 資料型別資訊，請參閱驅動程式的文件。  
  
 *m_nPrecision*  
 欄位的最大有效位數。 如需詳細資訊，請參閱 「 有效位數、 小數位數、 長度和顯示大小 」 中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m_nScale*  
 欄位的小數位數。 如需詳細資訊，請參閱 「 有效位數、 小數位數、 長度和顯示大小 」 中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m_nNullability*  
 是否欄位可接受 Null 值。 這可以是兩個值之一︰ **SQL_NULLABLE**欄位可接受 Null 值，如果或**SQL_NO_NULLS**如果欄位不接受 Null 值。  
  
## <a name="remarks"></a>備註  
 若要擷取這項資訊，請呼叫[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)



