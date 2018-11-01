---
title: CDaoIndexFieldInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 358e6654060e92e0df83b118fa70e1c3a3a990b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449578"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 結構

`CDaoIndexFieldInfo`結構包含的資料存取物件 (DAO) 定義索引欄位物件的相關資訊。

## <a name="syntax"></a>語法

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
唯一名稱的索引欄位物件。 如需詳細資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

*m_bDescending*<br/>
表示索引物件所定義的索引順序。 如果為遞減，則為 TRUE。

## <a name="remarks"></a>備註

Index 物件可以有數個欄位，指出 tabledef （或以資料表為基礎的資料錄集） 會編製索引的欄位。 上述的主要參考，表示在傳回的資訊是如何`m_pFieldInfos`隸屬[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)取得藉由呼叫物件`GetIndexInfo`類別成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或是[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。

索引物件和索引欄位的物件不是由 MFC 類別表示。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或是[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 每個索引物件，接著，會包含欄位物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或是您可以存取它們全部一次與`CDaoIndexInfo`藉由呼叫物件`GetIndexInfo`包含物件的成員函式。 `CDaoIndexInfo`物件，然後有一個資料成員， `m_pFieldInfos`，指向陣列`CDaoIndexFieldInfo`物件。

呼叫`GetIndexInfo`包含 tabledef 或資料錄集物件的集合是在索引中的成員函式會儲存您感興趣的索引物件。 然後，存取`m_pFieldInfos`隸屬[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)物件。 長度`m_pFieldInfos`陣列儲存在`m_nFields`。 `CDaoIndexFieldInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoIndexFieldInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

