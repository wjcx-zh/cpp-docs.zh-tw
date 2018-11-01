---
title: CDaoRelationFieldInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: 9a00d1cbaf58729863a85d4e9053c9241e9566ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599403"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 結構

`CDaoRelationFieldInfo`結構包含在關聯的資料存取物件 (DAO) 定義欄位的相關資訊。

## <a name="syntax"></a>語法

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
關聯的主要資料表中的欄位名稱。

*m_strForeignName*<br/>
關聯性的外部索引的資料表中的欄位名稱。

## <a name="remarks"></a>備註

DAO 關聯物件的主要資料表和外部資料表中定義關聯性的欄位中指定的欄位。 為上述的結構定義中的主要參考，表示在傳回的資訊是如何`m_pFieldInfos`隸屬[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件，藉由呼叫取得[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)類別成員函式`CDaoDatabase`。

MFC 類別並不表示關聯性物件和關聯性的欄位物件。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)包含稱為關聯性集合的關聯性物件的集合。 每個關聯性物件，接著，包含關聯欄位物件的集合。 每個關聯性的欄位物件相互關聯與外部索引資料表中的欄位，主要資料表中的欄位。 結合起來，關聯性的欄位物件定義一組欄位在每個資料表中，它定義了關聯性。 `CDaoDatabase` 可讓您存取與物件的關聯`CDaoRelationInfo`藉由呼叫物件`GetRelationInfo`成員函式。 `CDaoRelationInfo`物件，然後有一個資料成員， `m_pFieldInfos`，指向陣列`CDaoRelationFieldInfo`物件。

呼叫[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成員函式包含`CDaoDatabase`物件在其關聯集合會儲存您感興趣的關聯性物件。 然後，存取`m_pFieldInfos`隸屬[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件。 `CDaoRelationFieldInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoRelationFieldInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo 結構](../../mfc/reference/cdaorelationinfo-structure.md)
