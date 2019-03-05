---
title: CDaoRelationInfo 結構
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: 7d1c86732966d8222582dc6d4527af89963a5cdc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274969"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 結構

`CDaoRelationInfo`結構包含定義兩個資料表中的欄位之間的關聯性的相關資訊[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。

## <a name="syntax"></a>語法

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
唯一名稱的關聯性物件。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。

*m_strTable*<br/>
命名關聯性中的主資料表。

*m_strForeignTable*<br/>
命名關聯性中的外部資料表。 外部資料表是用來包含外部索引鍵的資料表。 一般而言，您可以使用外部資料表來建立，或強制執行參考完整性。 外部資料表通常是一對多關聯性的多邊。 外部資料表的範例包括包含美國的狀態或加拿大省或客戶訂單的程式碼的資料表。

*m_lAttributes*<br/>
包含關聯性類型的相關資訊。 這個成員的值可以是下列其中一項：

- `dbRelationUnique` 關聯性為一對一。

- `dbRelationDontEnforce` 關聯性不是強制執行 （沒有參考完整性）。

- `dbRelationInherited` 包含兩個連結的資料表的非目前資料庫中存在關聯性。

- `dbRelationLeft` 關聯性是左方的聯結。 左方外部聯結中包含的所有記錄，從第一個 （左側） 的兩個資料表，即使沒有相符的值，如第二個 （右側） 資料表中的記錄。

- `dbRelationRight` 關聯性是正確的聯結。 右方外部聯結包含所有記錄的第二個 （右側） 的兩個資料表，即使沒有相符的值，第一個 （左側） 中的記錄。

- `dbRelationUpdateCascade` 更新將會重疊顯示。

- `dbRelationDeleteCascade` 將串聯刪除。

*m_pFieldInfos*<br/>
陣列的指標[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)結構。 陣列包含關聯性中的每個欄位的一個物件。 `m_nFields`資料成員提供的陣列項目計數。

*m_nFields*<br/>
數目`CDaoRelationFieldInfo`中的物件`m_pFieldInfos`資料成員。

## <a name="remarks"></a>備註

主要和次要上述的參考會指出所傳回的資訊是如何[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)類別中的成員函式`CDaoDatabase`。

關聯的物件不以 MFC 類別來表示。 相反地，基礎的 MFC 物件的 DAO 物件`CDaoDatabase`類別會維護關聯性物件的集合：`CDaoDatabase`提供成員函式，來存取一些個別的項目關聯的詳細資訊，或者您可以存取它們全部一次使用`CDaoRelationInfo`藉由呼叫物件`GetRelationInfo`包含的資料庫物件的成員函式。

所擷取的資訊[CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成員函式會儲存在`CDaoRelationInfo`結構。 `CDaoRelationInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoRelationInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[CDaoRelationFieldInfo 結構](../../mfc/reference/cdaorelationfieldinfo-structure.md)
