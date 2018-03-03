---
title: "CDaoParameterInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3aabdb1dd59e1039f81d2ffe75c0d9e0770e43db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 結構
`CDaoParameterInfo`結構包含的資料存取物件 (DAO) 定義的參數物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一名稱的參數物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 `m_nType`  
 值，指出參數物件的資料類型。 如需可能值的清單，請參閱`m_nType`隸屬[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 如需詳細資訊，請參閱主題 DAO [說明] 中的 < 型別屬性 >。  
  
 *m_varValue*  
 參數的值，儲存在[COleVariant](../../mfc/reference/colevariant-class.md)物件。  
  
## <a name="remarks"></a>備註  
 主要和次要上述參考表示所傳回的資訊是如何[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)類別中的成員函式`CDaoQueryDef`。  
  
 MFC 不會封裝 DAO 類別中的參數物件。 DAO recordset 物件基礎的 MFC`CDaoQueryDef`物件儲存它們的參數集合中的參數。 若要存取中的參數物件[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件，呼叫 recordset 物件`GetParameterInfo`特定的參數名稱或索引插入參數集合的成員函式。 您可以使用[CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成員函式中搭配`GetParameterInfo`來循環參數集合。  
  
 所擷取的資訊[CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成員函式會儲存在`CDaoParameterInfo`結構。 呼叫`GetParameterInfo`recordset 物件的參數集合中儲存的參數物件。  
  
> [!NOTE]
>  如果您想要取得或設定參數的值，請使用[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)類別成員函式`CDaoRecordset`。  
  
 `CDaoParameterInfo`也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoParameterInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)
