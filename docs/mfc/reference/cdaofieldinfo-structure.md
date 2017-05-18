---
title: "CDaoFieldInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
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
ms.openlocfilehash: 15db0c56480dfefb9fc8806c08596e37c7d38eb2
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 結構
`CDaoFieldInfo`結構包含定義資料存取物件 (DAO) 的欄位物件的相關資訊。  
  
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
 `m_strName`  
 唯一名稱的欄位物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 `m_nType`  
 值，指出欄位的資料型別。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 型別屬性 」。 這個屬性的值可以是下列其中一項︰  
  
- **dbBoolean** Yes/No，與相同**TRUE**/**FALSE**  
  
- **dbByte**位元組  
  
- **dbInteger**短  
  
- **dbLong**長  
  
- **dbCurrency**貨幣，請參閱 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle**單一  
  
- **dbDouble** Double  
  
- **dbDate**日期/時間，請參閱 MFC 類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText**文字; 請參閱 MFC 類別[CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary**長二進位 （OLE 物件），您可能想要使用 MFC 類別[CByteArray](../../mfc/reference/cbytearray-class.md)而非類別`CLongBinary`為`CByteArray`更豐富、 更容易使用。  
  
- **dbMemo**附註，請參閱 MFC 類別`CString`  
  
- **dbGUID**全域唯一識別元/通用唯一識別項使用遠端程序呼叫。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 型別屬性 」。  
  
> [!NOTE]
>  請勿使用字串資料類型的二進位資料。 這會導致您通過 Unicode/ANSI 轉譯層，在更高額外負荷，而且可能是未預期的轉譯所產生的資料。  
  
 *m_lSize*  
 值，指出最大大小 （位元組） DAO field 物件，包含文字或包含文字或數值的欄位物件的固定的大小。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 大小屬性 」。 大小可以是下列值之一︰  
  
|類型|大小 (位元組)|描述|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 個位元組|是/否 （如同 True/False）|  
|**dbByte**|1|位元組|  
|**dbInteger**|2|整數|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|貨幣 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|日期/時間 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|文字 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|長度的二進位檔 （OLE 物件。[CByteArray](../../mfc/reference/cbytearray-class.md); 而不是使用`CLongBinary`)|  
|**dbMemo**|0|附註 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|全域唯一識別元/通用唯一識別項使用遠端程序呼叫。|  
  
 `m_lAttributes`  
 指定 tabledef、 資料錄集、 querydef 或索引物件所包含的欄位物件的特性。 傳回的值可以是加總這些常數，建立使用 c + + 位元 OR (**|**) 運算子︰  
  
- **dbFixedField**欄位大小固定的 （數值欄位的預設值）。  
  
- **dbVariableField**欄位大小是變數 （文字欄位）。  
  
- **dbAutoIncrField**新記錄的欄位值會自動遞增就無法變更的唯一長整數。 僅支援 Microsoft Jet 資料庫資料表。  
  
- **dbUpdatableField**可以變更欄位值。  
  
- **dbDescending**欄位以遞減排序 (Z-A 或 100-0) （僅適用於欄位物件的欄位集合中的索引物件; 在 MFC 中，物件本身包含在 tabledef 物件的索引） 的順序。 如果您省略這個常數，以遞增排序的欄位 (A-Z 或 0-100) 順序 （預設值）。  
  
 檢查此屬性設定，您可以使用 c + + 位元-和運算子 (**&**) 來測試特定的屬性。 當設定多個屬性，您可以組合運用這些使用位元 OR 結合適當的常數 (**|**) 運算子。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 屬性屬性 」。  
  
 *m_nOrdinalPosition*  
 值，指定您想要以 DAO 欄位物件表示要顯示相對於其他欄位的欄位的數字順序。 您可以設定這個屬性搭配[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 OrdinalPosition 屬性 」。  
  
 `m_bRequired`  
 指出 DAO 欄位物件是否需要非 Null 值。 如果這個屬性是**TRUE**，欄位不允許 Null 值。 如果所需的設定為**FALSE**，此欄位可以包含 Null 值，以及符合指定條件的零和驗證規則的屬性設定的值。 如需詳細資訊，請參閱主題 DAO 說明中的 「 必要屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_bAllowZeroLength*  
 指出是否為空字串 ("") 是 DAO 欄位物件具有文字或備忘資料類型的有效值。 如果這個屬性是**TRUE**，空字串是有效的值。 您可以將此屬性設定為**FALSE**是為了確保您無法使用空字串來設定欄位的值。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 允許零長度字串屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_lCollatingOrder`  
 適用於字串比較或排序文字中指定排序次序的順序。 如需詳細資訊，請參閱 「 自訂 Windows 登錄設定的資料存取 」 DAO 說明中的主題。 如需可能的值傳回的清單，請參閱**m_lCollatingOrder**成員[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)結構。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strForeignName`  
 指定的值，在關聯中，DAO 欄位中物件的外部資料表中對應至主資料表中的欄位名稱。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 ForeignName 屬性 」。  
  
 *m_strSourceField*  
 表示原始 DAO 欄位物件 tabledef、 資料錄集或 querydef 物件所包含的資料來源的欄位名稱。 這個屬性會指出原始欄位物件相關聯的欄位名稱。 例如，您可使用此屬性來判斷其名稱為基礎的資料表中的欄位名稱無關的查詢欄位中的資料的原始來源。 如需詳細資訊，請參閱 DAO 說明主題 「 SourceField SourceTable 屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strSourceTable*  
 表示原始 DAO 欄位物件 tabledef、 資料錄集或 querydef 物件所包含的資料來源的資料表名稱。 這個屬性會指出原始欄位物件相關聯的資料表名稱。 例如，您可使用此屬性來判斷其名稱為基礎的資料表中的欄位名稱無關的查詢欄位中的資料的原始來源。 如需詳細資訊，請參閱 DAO 說明主題 「 SourceField SourceTable 屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strValidationRule`  
 驗證欄位中的資料，因為它已變更或加入至資料表的值。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 ValidationRule 屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 如需 tabledefs 的相關資訊，請參閱**m_strValidationRule**成員[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構。  
  
 `m_strValidationText`  
 值，指定如果 DAO 欄位物件的值不符合驗證規則屬性設定所指定的驗證規則，會顯示您的應用程式之訊息的文字。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 驗證屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strDefaultValue*  
 DAO 欄位物件的預設值。 建立新的記錄時，預設值 屬性設定會自動做為值輸入欄位。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 DefaultValue 屬性 」。 您可以設定這個屬性與 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
## <a name="remarks"></a>備註  
 主要、 次要資料庫，且上述所有參考表示資訊由`GetFieldInfo`類別中的成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)， [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)，和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)。  
  
 Field 物件不會顯示由 MFC 類別。 相反地，下列類別的 MFC 物件的 DAO 物件包含的欄位物件的集合︰ [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 這些類別提供成員函式來存取欄位資訊的一些個別項目，或是您可以存取它們全部一次使用`CDaoFieldInfo`物件呼叫`GetFieldInfo`包含物件的成員函式。  
  
 除了用來檢查物件屬性，您也可以使用`CDaoFieldInfo`來建構在 tabledef 中建立新欄位的輸入的參數。 這項工作，有更簡單的選項，但如果您想要較細微的控制，您可以使用的版本[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)採用`CDaoFieldInfo`參數。  
  
 所擷取的資訊`GetFieldInfo`類別成員函式 （包含該欄位） 會儲存在`CDaoFieldInfo`結構。 呼叫`GetFieldInfo`欄位物件會儲存其欄位集合中包含物件的成員函式。 `CDaoFieldInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoFieldInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)


