---
title: CDaoIndexFieldInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7be9a6a9db842f1e80be62f48a9990cff36168e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 結構
`CDaoIndexFieldInfo`結構包含索引欄位物件定義的資料存取物件 (DAO) 的相關資訊。  
  
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
 唯一命名索引的欄位物件。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。  
  
 *m_bDescending*  
 表示索引物件所定義的索引順序。 **TRUE**如果會遞減順序。  
  
## <a name="remarks"></a>備註  
 索引物件可以有多個欄位，指出 tabledef （或以資料表為基礎的資料錄集） 已編製索引的欄位。 上述的主要參考表示在傳回的資訊是如何`m_pFieldInfos`隸屬[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)取得藉由呼叫物件`GetIndexInfo`類別成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引物件和索引欄位的物件未表示的 MFC 類別。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 每個索引物件，依序包含欄位物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或者您可以存取它們全部與`CDaoIndexInfo`藉由呼叫物件`GetIndexInfo`包含物件的成員函式。 `CDaoIndexInfo`物件，然後，具有資料成員， `m_pFieldInfos`，指向陣列`CDaoIndexFieldInfo`物件。  
  
 呼叫`GetIndexInfo`包含 tabledef 或資料錄集物件的集合是在索引中的成員函式會儲存您感興趣的索引物件。 然後，存取`m_pFieldInfos`隸屬[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)物件。 長度`m_pFieldInfos`陣列儲存在`m_nFields`。 `CDaoIndexFieldInfo` 也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoIndexFieldInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

