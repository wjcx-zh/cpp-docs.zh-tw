---
title: "CDaoRelationFieldInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
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
ms.openlocfilehash: 23d7497502f611cf2311e574556186dc5f7c7d3d
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 結構
`CDaoRelationFieldInfo`結構包含定義的資料存取物件 (DAO) 的關聯性中欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 關聯性的主資料表中的欄位名稱。  
  
 `m_strForeignName`  
 關聯性的外部索引資料表中的欄位名稱。  
  
## <a name="remarks"></a>備註  
 DAO 關聯物件的主要資料表和外部資料表中定義關聯性的欄位中指定的欄位。 在上述的結構定義主要參考表示中傳回資訊的方式`m_pFieldInfos`成員[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)取得藉由呼叫物件[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)類別成員函式`CDaoDatabase`。  
  
 關聯性物件和物件關聯欄位不會顯示由 MFC 類別。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)包含稱為關聯性集合的關聯性物件的集合。 每一個關聯性物件，包含關聯欄位物件的集合。 每個關聯的欄位物件相互關聯的主資料表中的欄位，與外部索引資料表中的欄位。 數位簽章物件關聯欄位定義欄位的群組中每個資料表，它定義了此關聯性。 `CDaoDatabase`可讓您存取與物件關聯`CDaoRelationInfo`物件呼叫`GetRelationInfo`成員函式。 `CDaoRelationInfo`物件，接著，必須為資料成員， `m_pFieldInfos`，指向陣列`CDaoRelationFieldInfo`物件。  
  
 呼叫[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成員函式包含`CDaoDatabase`物件在其關聯集合會儲存您感興趣的關聯性物件。 然後存取`m_pFieldInfos`成員[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件。 `CDaoRelationFieldInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoRelationFieldInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo 結構](../../mfc/reference/cdaorelationinfo-structure.md)

