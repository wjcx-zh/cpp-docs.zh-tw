---
title: "CDaoIndexFieldInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
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
ms.openlocfilehash: 975b3a704936adc9d4205938bb2c757ab650f0d9
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 結構
`CDaoIndexFieldInfo`結構包含索引欄位物件的定義資料存取物件 (DAO) 的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一命名索引的欄位物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 *m_bDescending*  
 表示索引物件所定義的索引順序。 **TRUE**如果順序會遞減排序。  
  
## <a name="remarks"></a>備註  
 索引物件可以有數個欄位，指出 tabledef （或以資料表為基礎的資料錄集） 已編製索引的欄位。 上述的主要參考表示在傳回的資訊是如何`m_pFieldInfos`成員[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)取得藉由呼叫物件`GetIndexInfo`類別成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引與索引欄位的物件不會顯示由 MFC 類別。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 每個索引物件，反而會包含欄位物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或是您可以存取它們全部一次使用`CDaoIndexInfo`物件呼叫`GetIndexInfo`包含物件的成員函式。 `CDaoIndexInfo`物件，接著，必須為資料成員， `m_pFieldInfos`，指向陣列`CDaoIndexFieldInfo`物件。  
  
 呼叫`GetIndexInfo`成員函式包含 tabledef 或資料錄集物件的集合是在索引中儲存您感興趣的索引物件。 然後存取`m_pFieldInfos`成員[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)物件。 長度`m_pFieldInfos`陣列儲存在`m_nFields`。 `CDaoIndexFieldInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoIndexFieldInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)


