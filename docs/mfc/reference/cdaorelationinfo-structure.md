---
title: "CDaoRelationInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7c3a8195aed2c3b3fe5c78c98afcc6e72a83cc21
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 結構
`CDaoRelationInfo`結構包含定義兩個資料表中的欄位之間的關聯性的相關資訊[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();
*// Constructor  
    CString m_strName;      // Primary  
    CString m_strTable;     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;        // Secondary *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一名稱的關聯物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 *m_strTable*  
 命名關聯性中的主要資料表。  
  
 *m_strForeignTable*  
 命名關聯性中的外部索引資料表。 外部資料表是用來包含外部索引鍵的資料表。 一般而言，您可以使用外部資料表來建立或強制參考完整性。 外部資料表通常是一對多關聯性的多邊。 外部資料表的範例包括包含程式碼狀態美國或加拿大地區或客戶訂單的資料表。  
  
 `m_lAttributes`  
 包含關聯性類型的相關資訊。 這個成員的值可以是下列其中一項︰  
  
- **dbRelationUnique**關聯性是一對一。  
  
- **dbRelationDontEnforce**關聯性不是強制執行 （沒有參考完整性）。  
  
- **dbRelationInherited**包含兩個連結的資料表的非資料庫中存在關聯性。  
  
- **dbRelationLeft**的關聯性是左方的聯結。 左外部聯結包含所有記錄的第一個 （左） 兩個資料表，即使沒有相符值的第二個 （右） 資料表中的記錄。  
  
- **dbRelationRight**的關聯性是正確的聯結。 右外部聯結包含所有記錄的第二個 （右） 的兩個資料表，即使沒有相符值的第一個 （左） 資料表中的記錄。  
  
- **dbRelationUpdateCascade**會串聯更新。  
  
- **dbRelationDeleteCascade**會串聯刪除。  
  
 `m_pFieldInfos`  
 陣列的指標[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)結構。 陣列包含關聯性中每個欄位的一個物件。 `m_nFields`資料成員可讓陣列項目的計數。  
  
 `m_nFields`  
 數目`CDaoRelationFieldInfo`物件`m_pFieldInfos`資料成員。  
  
## <a name="remarks"></a>備註  
 主要和次要上述參考表示資訊由[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)類別中的成員函式`CDaoDatabase`。  
  
 關聯性物件不會由 MFC 類別表示。 改為基礎的 MFC 物件的 DAO 物件、`CDaoDatabase`類別會維護關聯性物件的集合︰`CDaoDatabase`提供成員函式，以存取某些個別的項目關聯性的詳細資訊，或者，您可以存取它們全部一次與`CDaoRelationInfo`物件呼叫`GetRelationInfo`包含資料庫物件的成員函式。  
  
 所擷取的資訊[CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成員函式會儲存在`CDaoRelationInfo`結構。 `CDaoRelationInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoRelationInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [CDaoRelationFieldInfo 結構](../../mfc/reference/cdaorelationfieldinfo-structure.md)

