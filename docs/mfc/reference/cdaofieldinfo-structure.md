---
title: CDaoFieldInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: e98f5ba69f6702dd768cfe6605f993064e1b896c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096106"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 結構

`CDaoFieldInfo`結構包含針對資料存取物件（DAO）定義之欄位物件的相關資訊。

DAO 受到 Office 2013 的支援。 DAO 3.6 是最終版本，並被視為已淘汰。

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
唯一命名欄位物件。 如需詳細資訊，請參閱 DAO 說明中的「名稱屬性」主題。

*m_nType*<br/>
值，指出欄位的資料類型。 如需詳細資訊，請參閱 DAO 說明中的「類型屬性」主題。 這個屬性的值可以是下列其中一項：

- `dbBoolean`是/否，與 TRUE/FALSE 相同

- `dbByte`節

- `dbInteger`短缺

- `dbLong`前提

- `dbCurrency`符號請參閱 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`單機

- `dbDouble`兩

- `dbDate`日期/時間;請參閱 MFC 類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`文字請參閱 MFC 類別[CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`長二進位（OLE 物件）;您可能想要使用 MFC 類別[CByteArray](../../mfc/reference/cbytearray-class.md) ，而不`CLongBinary`是`CByteArray`類別，因為更豐富且更容易使用。

- `dbMemo`備忘請參閱 MFC 類別`CString`

- `dbGUID`與遠端程序呼叫搭配使用的全域唯一識別碼/通用唯一識別碼。 如需詳細資訊，請參閱 DAO 說明中的「類型屬性」主題。

> [!NOTE]
>  請勿針對二進位資料使用字串資料類型。 這會導致您的資料通過 Unicode/ANSI 轉譯層，因而增加額外負荷，而且可能會產生非預期的翻譯。

*m_lSize*<br/>
值，指出 DAO 欄位物件的大小上限（以位元組為單位），其中包含文字或包含文字或數值之欄位物件的固定大小。 如需詳細資訊，請參閱 DAO 說明中的「大小屬性」主題。 大小可以是下列其中一個值：

|類型|大小 (位元組)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|是/否（與 True/False 相同）|
|`dbByte`|1|Byte|
|`dbInteger`|2|整數|
|`dbLong`|4|Long|
|`dbCurrency`|8|貨幣（[COleCurrency](../../mfc/reference/colecurrency-class.md)）|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日期/時間（[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)）|
|`dbText`|1 - 255|文字（[CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbLongBinary`|0|長二進位（OLE 物件;）[CByteArray](../../mfc/reference/cbytearray-class.md);使用， `CLongBinary`而不是）|
|`dbMemo`|0|備忘錄（[CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbGUID`|16|與遠端程序呼叫搭配使用的全域唯一識別碼/通用唯一識別碼。|

*m_lAttributes*<br/>
指定 tabledef、記錄集、querydef 或索引物件所包含之欄位物件的特性。 傳回的值可以是這些常數的總和，並使用C++位 or （ **&#124;** ）運算子來建立：

- `dbFixedField`欄位大小是固定的（數值欄位的預設值）。

- `dbVariableField`[欄位大小] 為 [變數] （僅限文字欄位）。

- `dbAutoIncrField`新記錄的域值會自動遞增為不能變更的唯一長整數。 僅支援 Microsoft Jet 資料庫資料表。

- `dbUpdatableField`域值可以變更。

- `dbDescending`欄位是以遞減（Z-A 或 100-0）順序排序（僅適用于索引物件的 Fields 集合中的欄位物件; 在 MFC 中，索引物件本身包含在 tabledef 物件中）。 如果您省略此常數，則會以遞增（a-z 或 0-100）順序（預設值）排序欄位。

檢查這個屬性的設定時，您可以使用C++位 and 運算子（ **&** ）來測試特定屬性。 設定多個屬性時，您可以結合適當的常數與位 OR （ **&#124;** ）運算子，將它們結合在一起。 如需詳細資訊，請參閱 DAO 說明中的「屬性屬性」主題。

*m_nOrdinalPosition*<br/>
值，指定要顯示與其他欄位相關的 DAO 欄位物件所代表之欄位的數值順序。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定此屬性。 如需詳細資訊，請參閱 DAO 說明中的「OrdinalPosition 屬性」主題。

*m_bRequired*<br/>
表示 DAO 欄位物件是否需要非 Null 值。 如果此屬性為 TRUE，則欄位不允許 Null 值。 如果 [必要] 設定為 [FALSE]，則欄位可以包含 Null 值，以及符合 [字串類型] 和 [ValidationRule] 屬性設定所指定之條件的值。 如需詳細資訊，請參閱 DAO 說明中的「必要屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_bAllowZeroLength*<br/>
指出空字串（""）是否為具有 Text 或 Memo 資料類型之 DAO 欄位物件的有效值。 如果此屬性為 TRUE，則空字串是有效的值。 您可以將此屬性設定為 FALSE，以確保您無法使用空字串來設定欄位的值。 如需詳細資訊，請參閱 DAO 說明中的「字串屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_lCollatingOrder*<br/>
指定文字中的排序次序順序，以進行字串比較或排序。 如需詳細資訊，請參閱 DAO 說明中的「自訂資料存取的 Windows 登錄設定」主題。 如需傳回可能值的清單，請參閱`m_lCollatingOrder` [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)結構的成員。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_strForeignName*<br/>
在關聯性中，值會指定外部資料表中，對應至主資料表中之欄位的 DAO 欄位物件名稱。 如需詳細資訊，請參閱 DAO 說明中的「ForeignName 屬性」主題。

*m_strSourceField*<br/>
指出欄位的名稱，這是 tabledef、記錄集或 querydef 物件所包含的 DAO 欄位物件之資料的原始來源。 這個屬性會指出與欄位物件相關聯的原始功能變數名稱。 例如，您可以使用這個屬性來判斷查詢欄位中資料的原始來源，其名稱與基礎資料表中的功能變數名稱無關。 如需詳細資訊，請參閱 DAO 說明中的「SourceField，SourceTable 屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_strSourceTable*<br/>
指出資料表的名稱，這是 tabledef、記錄集或 querydef 物件所包含的 DAO 欄位物件之資料的原始來源。 這個屬性會指出與欄位物件相關聯的原始資料表名稱。 例如，您可以使用這個屬性來判斷查詢欄位中資料的原始來源，其名稱與基礎資料表中的功能變數名稱無關。 如需詳細資訊，請參閱 DAO 說明中的「SourceField，SourceTable 屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_strValidationRule*<br/>
值，會在欄位變更或加入至資料表時，驗證其資料。 如需詳細資訊，請參閱 DAO 說明中的「ValidationRule 屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

如需 tabledefs 的相關資訊，請`m_strValidationRule`參閱[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構的成員。

*m_strValidationText*<br/>
值，指定當 DAO 欄位物件的值無法滿足 [ValidationRule] 屬性設定所指定的驗證規則時，您的應用程式所顯示的訊息文字。 如需詳細資訊，請參閱 DAO 說明中的「有效性屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

*m_strDefaultValue*<br/>
DAO 欄位物件的預設值。 建立新記錄時，會自動輸入 DefaultValue 屬性設定做為欄位的值。 如需詳細資訊，請參閱 DAO 說明中的「DefaultValue 屬性」主題。 您可以使用[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)來設定 tabledef 的這個屬性。

## <a name="remarks"></a>備註

主要、次要和以上的`GetFieldInfo`參考會指出成員函式在類別[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)、 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)中傳回信息的方式。

欄位物件不是以 MFC 類別表示。 相反地，下列類別的基本 MFC 物件的 DAO 物件包含 field 物件的集合：[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 這些類別會提供成員函式來存取欄位資訊的某些個別專案，或者您可以`CDaoFieldInfo` `GetFieldInfo`呼叫包含物件的成員函式，一次使用物件來存取它們。

除了用來檢查物件屬性之外，您也可以使用`CDaoFieldInfo`來建立 tabledef 中建立新欄位的輸入參數。 這項工作有更簡單的選項，但如果您想要更精細的控制，您可以使用採用`CDaoFieldInfo`參數的[CDaoTableDef：： CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)版本。

成員函式所抓取的資訊（屬於包含欄位的類別）會儲存`CDaoFieldInfo`在結構中。 `GetFieldInfo` 呼叫中包含物件的成員函式，其欄位集合會儲存欄位物件。`GetFieldInfo` `CDaoFieldInfo`也會定義`Dump` debug 組建中的成員函式。 您可以使用`Dump`來傾印`CDaoFieldInfo`物件的內容。

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
