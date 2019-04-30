---
title: CDaoIndexInfo 結構
ms.date: 06/25/2018
f1_keywords:
- CDaoIndexInfo
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
ms.openlocfilehash: 55f64fcebc308bd0e63643cfb5447608c4e2e37c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399768"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 結構

`CDaoIndexInfo`結構包含定義資料存取物件 (DAO) 的索引物件的相關資訊。

## <a name="syntax"></a>語法

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>參數

*m_strName*<br/>
唯一地命名欄位的物件。 如需詳細資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

*m_pFieldInfos*<br/>
陣列的指標[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md)指出哪些 tabledef 或資料錄集欄位在索引中的索引鍵欄位的物件。 每個物件會識別在索引中的一個欄位。 預設索引順序為遞增。 Index 物件可以有一或多個代表每一筆記錄的索引鍵的欄位。 這些可以遞增、 遞減或組合。

*m_nFields*<br/>
儲存在欄位數目`m_pFieldInfos`。

*m_bPrimary*<br/>
如果主要屬性為 TRUE，則索引物件表示主要索引。 主索引鍵是由一或多個可唯一識別預先定義的順序中的資料表中的所有記錄的欄位所組成。 索引欄位必須是唯一的因為索引物件的唯一屬性也會設定為 TRUE，在 DAO 中。 如果主索引鍵是由多個欄位所組成，每個欄位可以包含重複的值，但每個組合的所有索引的欄位值必須是唯一。 主要索引資料表的索引鍵所組成，而且通常包含相同的主索引鍵的欄位。

當您設定資料表的主索引鍵時，則主索引鍵都會自動定義為資料表的主索引中。 如需詳細資訊，請參閱 「 主要屬性 」 和 DAO [說明] 中的 < 唯一屬性 > 主題。

> [!NOTE]
> 有，最多可達，資料表上的一個主要索引。

*m_bUnique*<br/>
表示索引物件是否表示資料表的唯一索引。 如果這個屬性為 TRUE，則索引物件表示是唯一的索引。 唯一的索引是由一或多個以邏輯方式排列的資料表中唯一的而預先定義的順序中的所有記錄的欄位所組成。 如果索引是由一個欄位所組成，該欄位中的值必須是唯一的整個資料表。 如果索引是由多個欄位所組成，每個欄位可以包含重複的值，但每個組合的所有索引的欄位值必須是唯一。

索引物件的唯一和主要屬性會設為 TRUE，如果索引是唯一和主要：它會唯一識別預先定義的邏輯順序中的資料表中的所有記錄。 如果主要的屬性設定為 FALSE，則索引是次要索引。 次要索引 （索引鍵和非索引鍵） 以邏輯方式排列中預先定義的順序記錄，而不做為資料表中記錄的識別碼。

如需詳細資訊，請參閱 「 主要屬性 」 和 DAO [說明] 中的 < 唯一屬性 > 主題。

*m_bClustered*<br/>
表示索引物件是否表示資料表的叢集的索引。 Index 物件如果這個屬性為 TRUE，表示叢集的索引;否則，則沒有。 叢集的索引包含一或多個非索引鍵欄位，結合起來，排列預先定義的順序中的資料表中的所有記錄。 具有叢集索引，資料表中的資料會解譯為常值會儲存在叢集索引所指定的順序。 叢集的索引會提供有效率地存取資料表中的記錄。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 叢集屬性 」。

> [!NOTE]
> 使用 Microsoft Jet 資料庫引擎，因為 Jet database engine 不支援叢集的索引的資料庫，會忽略的 Clustered 屬性。

*m_bIgnoreNulls*<br/>
指出是否有 Null 值，其索引欄位中的資料錄的索引項目。 如果這個屬性為 TRUE，表示具有 Null 值的欄位中沒有索引項目。 若要讓搜尋更快的使用欄位的記錄，您可以定義欄位的索引。 如果您允許 Null 索引的欄位中的項目，並預期有許多為 Null 的項目，您可以設定的索引物件的忽略 Null 屬性為 TRUE，以減少索引所使用的儲存體空間數量。 忽略 Null 屬性設定和必要的屬性設定一起決定了 Null 的索引值記錄是否具有索引項目，如下表所示。

|IgnoreNulls|必要|索引欄位都是 null|
|-----------------|--------------|-------------------------|
|True|False|允許的 null 值新增沒有索引項目。|
|False|False|允許的 null 值已加入的索引項目。|
|True 或 False|True|不允許 null 值新增沒有索引項目。|

如需詳細資訊，請參閱主題 DAO [說明] 中的 < 忽略 Null 屬性 >。

*m_bRequired*<br/>
指出 DAO index 物件是否需要非 Null 值。 如果這個屬性為 TRUE，index 物件不允許 Null 值。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 所需屬性 」。

> [!TIP]
> 當您可以設定此欄位物件 （包含由 tabledef、 資料錄集或 recordset 物件） 或 DAO index 物件的屬性時，則會設定欄位的物件。 Field 物件的屬性設定的有效性是之前的索引物件進行檢查。

*m_bForeign*<br/>
表示索引物件是否表示資料表中的外部索引鍵。 如果這個屬性為 TRUE，則索引會代表資料表中的外部索引鍵。 外部索引鍵是由一或多個外部資料表中唯一識別欄位中的主要資料表的資料列所組成。 Microsoft Jet 資料庫引擎會建立外部資料表的索引物件，並設定外部索引的屬性，當您建立的強制執行參考完整性的關聯性。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 外部索引屬性 」。

*m_lDistinctCount*<br/>
表示 index 物件相關聯的資料表中包含的唯一值數目。 檢查 DistinctCount; 屬性來判斷唯一的值或在索引中的金鑰數目。 任何索引鍵是只計算一次，即使有可能會多次出現的值如果索引允許重複的值。 這項資訊可用於進行最佳化的資料存取，藉由評估索引資訊的應用程式。 唯一值數目就是所謂的索引物件的基數。 [DistinctCount] 屬性將不一定會反映實際數目的索引鍵在特定時間。 例如，進行交易回復所造成的變更將不會立即反映在 [DistinctCount] 屬性。 如需詳細資訊，請參閱主題 DAO [說明] 中的 < DistinctCount 屬性 >。

## <a name="remarks"></a>備註

主要、 次要資料庫，且上述所有的參考會指出所傳回的資訊是如何`GetIndexInfo`類別中的成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)並[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。

索引物件未表示的 MFC 類別。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或是[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或是您可以存取它們全部一次與`CDaoIndexInfo`藉由呼叫物件`GetIndexInfo`包含物件的成員函式。

`CDaoIndexInfo` 具有建構函式和解構函式，才能正確地配置和解除配置中的索引欄位資訊`m_pFieldInfos`。

所擷取的資訊`GetIndexInfo`tabledef 物件成員函式會儲存在`CDaoIndexInfo`結構。 呼叫`GetIndexInfo`包含 tabledef 物件的索引集合中儲存的索引物件的成員函式。 `CDaoIndexInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoIndexInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
