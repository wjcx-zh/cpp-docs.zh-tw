---
title: CDaoFieldInfo 結構
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368403"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 結構

該`CDaoFieldInfo`結構包含有關為數據存取物件 (DAO) 定義的欄位物件的資訊。

通過 Office 2013 支援 DAO。 DAO 3.6 是最終版本,它被視為過時版本。

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
唯一地命名字段物件。 有關詳細資訊,請參閱 DAO 説明中的主題"名稱屬性"。

*m_nType*<br/>
指示欄位數據類型的值。 有關詳細資訊,請參閱 DAO 説明中的主題"類型屬性"。 此屬性的值可以是以下值之一:

- `dbBoolean`是/否,與 TRUE/FALSE 相同

- `dbByte`位元組

- `dbInteger`短

- `dbLong`長

- `dbCurrency`貨幣;請參考 MFC 類別[COle 貨幣](../../mfc/reference/colecurrency-class.md)

- `dbSingle`單

- `dbDouble`雙

- `dbDate`日期/時間;請參考 MFC 類別[COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`文字;請參閱 MFC 類別[CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`長二進制(OLE 物件);您可能希望使用 MFC 類[CByteArray](../../mfc/reference/cbytearray-class.md)而不是類`CLongBinary`,`CByteArray`因為更豐富、更易於使用。

- `dbMemo`備忘錄;請參閱 MFC 類別`CString`

- `dbGUID`與遠端過程呼叫一起使用的全域唯一標識符/通用唯一標識符。 有關詳細資訊,請參閱 DAO 説明中的主題"類型屬性"。

> [!NOTE]
> 不要對二進位數據使用字串資料類型。 這將導致數據通過 Unicode/ANSI 翻譯層,從而導致開銷增加,並可能導致意外的翻譯。

*m_lSize*<br/>
指示包含文本或包含文本或數值的欄位物件的固定大小的 DAO 欄位物件的最大大小(以位元組為單位)的值。 有關詳細資訊,請參閱 DAO 説明中的主題"大小屬性"。 大小可以是以下值之一:

|類型|大小 (位元組)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|是/否(與真/假相同)|
|`dbByte`|1|Byte|
|`dbInteger`|2|整數|
|`dbLong`|4|long|
|`dbCurrency`|8|貨幣 ([COle 金錢](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日期/時間 ([COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|文字 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|長二進位(OLE物件;[CBytearray](../../mfc/reference/cbytearray-class.md);使用而不是`CLongBinary`。|
|`dbMemo`|0|備忘錄 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|與遠端過程呼叫一起使用的全域唯一標識符/通用唯一標識符。|

*m_lAttributes*<br/>
指定表def、記錄集、查詢def或索引物件中包含的欄位物件的特徵。 傳回的值可以是這些常量的總和,這些常量是使用C++位元或 (**&#124;**) 運算子建立的:

- `dbFixedField`欄位大小是固定的(數位欄位的預設值)。

- `dbVariableField`欄位大小是可變的(僅限文字欄位)。

- `dbAutoIncrField`新記錄的欄位值將自動遞增為無法更改的唯一長整數。 僅支援 Microsoft Jet 資料庫表。

- `dbUpdatableField`可以更改欄位值。

- `dbDescending`欄位按降序(Z - A 或 100 - 0)順序排序(僅適用於索引物件的欄位集合中的欄位物件;在 MFC 中,索引物件本身包含在 tabledef 物件中)。 如果省略此常量,則欄位按升序(A - Z 或 0 - 100)順序排序(預設值)。

檢查此屬性的設定時,可以使用C++位 - AND 運算**&** 符 ( ) 來測試特定屬性。 設置多個屬性時,可以通過將適當的常量與位 OR** (&#124;)** 運算符組合來組合它們。 有關詳細資訊,請參閱 DAO 説明中的主題「屬性屬性」。

*m_nOrdinalPosition*<br/>
指定希望 DAO 欄位物件表示的欄位相對於其他欄位顯示的數位順序的值。 您可以使用[CDaoTableDef 設定這個屬性:建立欄位](../../mfc/reference/cdaotabledef-class.md#createfield)。 有關詳細資訊,請參閱 DAO 説明中的主題"位置屬性」。。

*m_bRequired*<br/>
指示 DAO 欄位物件是否需要非 Null 值。 如果此屬性為 TRUE,則該欄位不允許 Null 值。 如果「必需」設定為 FALSE,則該欄位可以包含 Null 值以及滿足「允許零長度」和「驗證規則」屬性設置指定的條件的值。 有關詳細資訊,請參閱 DAO 説明中的主題"必需屬性"。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_bAllowZeroLength*<br/>
指示空字串 ("") 是否是具有文本或備忘錄數據類型的 DAO 欄位物件的有效值。 如果此屬性為 TRUE,則空字串是有效的值。 可以將此屬性設置為 FALSE,以確保不能使用空字串來設置欄位的值。 有關詳細資訊,請參閱 DAO 説明中的主題"允許零長度屬性」。。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_lCollatingOrder*<br/>
指定文字中排序順序的順序,用於字串比較或排序。 有關詳細資訊,請參閱 DAO 説明中的主題"為數據訪問自定義 Windows 註冊表設置"。 有關返回的可能值的清單,請參閱`m_lCollatingOrder`[CDao 資料庫資訊](../../mfc/reference/cdaodatabaseinfo-structure.md)結構的成員。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_strForeignName*<br/>
在關係中指定與主表中的欄位對應的外表中的 DAO 欄位物件的名稱的值。 有關詳細資訊,請參閱 DAO 説明中的"外名屬性"主題。

*m_strSourceField*<br/>
指示欄位的名稱,該欄位是表def、記錄集或查詢def物件中包含的DAO欄位物件的原始資料來源。 此屬性指示與欄位物件關聯的原始欄位名稱。 例如,可以使用此屬性確定查詢欄位中的數據的原始源,其名稱與基礎表中的欄位名稱無關。 有關詳細資訊,請參閱 DAO 説明中的主題「源欄位、源表屬性」。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_strSourceTable*<br/>
指示表的名稱,該表是表def、記錄集或查詢def物件中包含的DAO欄位物件的原始數據源。 此屬性指示與欄位物件關聯的原始表名稱。 例如,可以使用此屬性確定查詢欄位中的數據的原始源,其名稱與基礎表中的欄位名稱無關。 有關詳細資訊,請參閱 DAO 説明中的主題「源欄位、源表屬性」。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_strValidationRule*<br/>
在欄位中更改或添加到表中的資料時驗證資料的值。 有關詳細資訊,請參閱 DAO 説明中的主題"驗證規則屬性」。。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

有關表defs的相關信息,請參閱`m_strValidationRule`[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構的成員。

*m_strValidationText*<br/>
如果 DAO 欄位物件的值不符合驗證規則屬性設置指定的驗證規則,則指定應用程式顯示的消息文本的值。 有關詳細資訊,請參閱 DAO 説明中的主題「驗證文本屬性」。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

*m_strDefaultValue*<br/>
DAO 欄位物件的預設值。 建立新記錄時,預設值屬性設置將自動輸入為欄位的值。 有關詳細資訊,請參閱 DAO 説明中的主題"默認值屬性」。。 您可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)為表def設定此屬性。

## <a name="remarks"></a>備註

`GetFieldInfo`對上述主要、次要和全部的引用指示成員函數如何返回[CDaoTableDef、CDaoQueryDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)中的成員函數。

欄位物件不由 MFC 類表示。 相反,以下類別 MFC 物件的基礎 DAO 物件包含欄位物件的集合[:CDaoTableDef、CDaoRecordset](../../mfc/reference/cdaotabledef-class.md)和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 這些類提供成員函數以造訪欄位資訊的一些單個項,或者您可以通過調用`CDaoFieldInfo``GetFieldInfo`包含物件的成員函數同時使用對象訪問它們。

除了用於檢查物件屬性外,您還可以使用`CDaoFieldInfo`建構輸入參數以在 tabledef 中建立新欄位。 更簡單的選項可用於此任務,但如果需要更精細的控制,可以使用[CDaoTableDef::createField](../../mfc/reference/cdaotabledef-class.md#createfield)採用`CDaoFieldInfo`參數的版本。

`GetFieldInfo`成員函數(包含欄位的類)檢索的資訊存儲`CDaoFieldInfo`在結構中。 調用包含`GetFieldInfo`對象的成員函數,其中欄位集合中儲存欄位物件。 `CDaoFieldInfo`還在調試生成中`Dump`定義成員函數。 可以使用`Dump`轉`CDaoFieldInfo`儲 對象的內容。

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:取得菲爾德資訊](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset:取得菲爾德資訊](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef:取得菲爾德資訊](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
