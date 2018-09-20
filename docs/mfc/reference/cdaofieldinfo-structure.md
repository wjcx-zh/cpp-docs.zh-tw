---
title: CDaoFieldInfo 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaf3f41bf6a6fe5d67ec5835d57889f6ec7dbae6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437676"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 結構

`CDaoFieldInfo`結構包含的資料存取物件 (DAO) 定義的欄位物件的相關資訊。

## <a name="syntax"></a>語法

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>參數

*m_strName*<br/>
唯一地命名欄位的物件。 如需詳細資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

*m_nType*<br/>
值，指出欄位的資料類型。 如需詳細資訊，請參閱 DAO [說明] 中的 「 型別屬性 」。 這個屬性的值可以是下列其中一項：

- `dbBoolean` 是/否，相同一個 TRUE/FALSE

- `dbByte` 位元組

- `dbInteger` 簡短

- `dbLong` 長

- `dbCurrency` 貨幣;請參閱 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` 單一

- `dbDouble` 雙精度浮點數

- `dbDate` 日期/時間;請參閱 MFC 類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` 文字;請參閱 MFC 類別[CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` 長二進位檔 （OLE 物件）;您可能想要使用 MFC 類別[CByteArray](../../mfc/reference/cbytearray-class.md)而不是類別`CLongBinary`做為`CByteArray`更豐富、 更輕易地使用。

- `dbMemo` 備忘錄;請參閱 MFC 類別 `CString`

- `dbGUID` 全域唯一識別項/識別碼 Universally Unique Identifier 搭配遠端程序呼叫。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 型別屬性 」。

> [!NOTE]
>  請勿用於二進位資料的字串資料類型。 這會導致您的資料將會透過 Unicode/ANSI 轉譯層，導致更高額外負荷，而且可能是未預期的轉譯。

*m_lSize*<br/>
值，指出最大的大小，以位元組為單位，DAO 欄位物件，其中包含文字或包含文字或數值的欄位物件的固定的大小。 如需詳細資訊，請參閱 DAO [說明] 中的 「 大小屬性 」。 大小可以是下列值之一：

|類型|大小 (位元組)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|是/否 （如同 True/False）|
|`dbByte`|1|Byte|
|`dbInteger`|2|整數|
|`dbLong`|4|Long|
|`dbCurrency`|8|貨幣 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日期/時間 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|文字 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|長二進位檔 (OLE Object;[CByteArray](../../mfc/reference/cbytearray-class.md); 而不是使用`CLongBinary`)|
|`dbMemo`|0|備忘 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|全域唯一識別項/識別碼 Universally Unique Identifier 搭配遠端程序呼叫。|

*m_lAttributes*<br/>
指定 tabledef、 資料錄集、 querydef 或索引物件所包含的欄位物件的特性。 傳回的值可以是加總這些常數，建立使用 c + + 位元 OR (**&#124;**) 運算子：

- `dbFixedField` 欄位大小被固定的 （數值欄位的預設值）。

- `dbVariableField` 欄位大小是變數 （文字欄位）。

- `dbAutoIncrField` 新的資料錄的欄位值無法變更的唯一的長整數，會自動遞增。 僅支援 Microsoft Jet 資料庫資料表。

- `dbUpdatableField` 可以變更欄位值。

- `dbDescending` 欄位以遞減排序 (Z-A 或 100-0) （僅適用於欄位物件的索引物件的欄位集合中; 在 MFC 中，物件本身包含在 tabledef 物件的索引） 的順序。 如果您省略這個常數時，欄位以遞增排序 (A-Z 或 0-100) 順序 （預設值）。

當檢查這個屬性的設定，您可以使用 c + + 位元-和運算子 (**&**) 來測試特定的屬性。 在設定多個屬性，您就可以將它們結合使用位元 OR 結合適當的常數 (**&#124;**) 運算子。 如需詳細資訊，請參閱 DAO [說明] 中的 「 屬性屬性 」。

*m_nOrdinalPosition*<br/>
值，指定您想要設定物件所表示 DAO 欄位要顯示相對於其他欄位的欄位數字順序。 您可以設定此屬性與[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。 如需詳細資訊，請參閱 DAO [說明] 中的 < OrdinalPosition 屬性 >。

*m_bRequired*<br/>
指出 DAO 欄位物件是否需要非 Null 值。 如果這個屬性為 TRUE，欄位不允許 Null 值。 視需要設定為 FALSE，此欄位只能包含 Null 值，以及符合條件允許零長度字串和驗證規則的屬性設定所指定的值。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 所需屬性 」。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_bAllowZeroLength*<br/>
指出是否為空字串 ("") 是具有文字或備忘資料類型的 DAO 欄位物件的有效的值。 如果這個屬性為 TRUE，則為空字串會是有效的值。 您可以設定此屬性為 FALSE，以確保您無法使用空字串來設定欄位的值。 如需詳細資訊，請參閱 DAO [說明] 中的 「 允許零長度字串屬性 」。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_lCollatingOrder*<br/>
指定文字字串比較或排序的排序次序的順序。 如需詳細資訊，請參閱本主題中的 < 自訂 Windows 登錄設定的資料存取 」 DAO 幫助。 如需可能的值傳回的清單，請參閱 <<c0> `m_lCollatingOrder` 隸屬[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)結構。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strForeignName*<br/>
指定的值，在關聯，DAO 欄位中物件的外部資料表中對應至主要資料表中的欄位名稱。 如需詳細資訊，請參閱 DAO [說明] 中的 < ForeignName 屬性 >。

*m_strSourceField*<br/>
表示原始來源的 DAO 欄位物件 tabledef、 資料錄集或 recordset 物件所包含的資料欄位的名稱。 這個屬性指出欄位物件相關聯的原始欄位名稱。 例如，您可以使用這個屬性來判斷其名稱是不相關的基礎資料表中的欄位名稱的查詢欄位中的資料的原始來源。 如需詳細資訊，請參閱 DAO 說明主題 「 SourceField SourceTable 屬性 」。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strSourceTable*<br/>
指出 tabledef、 資料錄集或 recordset 物件所包含的 DAO 欄位物件的資料的原始來源的資料表名稱。 這個屬性會指出原始欄位物件相關聯的資料表名稱。 例如，您可以使用這個屬性來判斷其名稱是不相關的基礎資料表中的欄位名稱的查詢欄位中的資料的原始來源。 如需詳細資訊，請參閱 DAO 說明主題 「 SourceField SourceTable 屬性 」。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strValidationRule*<br/>
值，這個值會驗證欄位中的資料，因為它已變更或加入至資料表。 如需詳細資訊，請參閱 DAO [說明] 中的 < ValidationRule 屬性 >。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

如需相關 tabledefs 的詳細資訊，請參閱`m_strValidationRule`隸屬[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構。

*m_strValidationText*<br/>
值，指定如果 DAO 欄位物件的值不符合驗證規則的屬性設定所指定的驗證規則，會顯示您的應用程式之訊息的文字。 如需詳細資訊，請參閱 DAO [說明] 中的 < 驗證文字屬性 >。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strDefaultValue*<br/>
DAO 欄位物件的預設值。 建立新的記錄時，預設值 屬性設定會自動輸入的值，欄位。 如需詳細資訊，請參閱 DAO [說明] 中的 < DefaultValue 屬性 >。 您可以設定此屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

## <a name="remarks"></a>備註

主要、 次要資料庫，且上述所有的參考會指出所傳回的資訊是如何`GetFieldInfo`類別中的成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)， [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)，和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)。

欄位的物件不以 MFC 類別來表示。 相反地，下列類別的 MFC 物件的 DAO 物件包含的欄位物件的集合： [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，並[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 這些類別提供成員函式，若要存取的欄位資訊，一些個別項目，或是您可以存取它們全部一次與`CDaoFieldInfo`藉由呼叫物件`GetFieldInfo`包含物件的成員函式。

除了檢查物件屬性使用，您也可以使用`CDaoFieldInfo`建構 tabledef 中建立新欄位的輸入的參數。 這項工作，有更簡單的選項，但如果想要更細微的控制，您可以使用新版[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)採用`CDaoFieldInfo`參數。

所擷取的資訊`GetFieldInfo`成員函式 （包含欄位的類別） 會儲存在`CDaoFieldInfo`結構。 呼叫`GetFieldInfo`欄位物件會儲存在其欄位集合中包含物件的成員函式。 `CDaoFieldInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoFieldInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)

