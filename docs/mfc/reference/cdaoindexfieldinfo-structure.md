---
title: CDaoIndexFieldInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303667"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 結構

`CDaoIndexFieldInfo` 結構包含針對資料存取物件（DAO）定義之索引欄位物件的相關資訊。

DAO 受到 Office 2013 的支援。 DAO 3.6 是最後的版本，被視為已淘汰。

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
唯一命名索引欄位物件。 如需詳細資訊，請參閱 DAO 說明中的「名稱屬性」主題。

*m_bDescending*<br/>
表示索引物件所定義的索引順序。 如果順序遞減，則為 TRUE。

## <a name="remarks"></a>備註

索引物件可以有數個欄位，指出 tabledef （或以資料表為基礎的記錄集）的欄位會編制索引。 上述主要的參考會指出如何在[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)物件的 `m_pFieldInfos` 成員中傳回信息，其是藉由呼叫[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)類別的 `GetIndexInfo` 成員函式取得。

索引物件和索引欄位物件不是以 MFC 類別表示。 相反地， [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)類別之基礎 MFC 物件的 DAO 物件，會包含索引物件的集合，稱為「索引」集合。 接著，每個索引物件都包含 field 物件的集合。 這些類別會提供成員函式來存取索引資訊的個別專案，或者您可以藉由呼叫包含物件的 `GetIndexInfo` 成員函式，一次使用 `CDaoIndexInfo` 物件來存取它們。 然後，`CDaoIndexInfo` 物件的資料成員 `m_pFieldInfos`，指向 `CDaoIndexFieldInfo` 物件的陣列。

在中，呼叫包含 tabledef 或 recordset 物件的 `GetIndexInfo` 成員函式，其索引集合會儲存您感興趣的索引物件。 然後存取[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)物件的 `m_pFieldInfos` 成員。 `m_pFieldInfos` 陣列的長度會儲存在 `m_nFields`中。 `CDaoIndexFieldInfo` 也會在 debug build 中定義 `Dump` 成員函式。 您可以使用 `Dump` 來傾印 `CDaoIndexFieldInfo` 物件的內容。

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef：： GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset：： GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
