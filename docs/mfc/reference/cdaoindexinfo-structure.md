---
title: CDaoIndexInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8c98181a9ec049308d7b85e57c028740927cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367031"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 結構
`CDaoIndexInfo`結構包含的資料存取物件 (DAO) 定義的索引物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一命名欄位的物件。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。  
  
 `m_pFieldInfos`  
 陣列的指標[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md)指出哪些 tabledef 或資料錄集欄位在索引中的索引鍵欄位的物件。 每個物件識別在索引中的一個欄位。 預設索引順序為遞增。 索引物件只能有一個或多個欄位代表每一筆記錄的索引鍵。 這些可以遞增、 遞減或組合。  
  
 `m_nFields`  
 儲存中的欄位數目`m_pFieldInfos`。  
  
 *m_bPrimary*  
 如果主要屬性為**TRUE**，index 物件表示主要索引。 主索引鍵是由一或多個唯一識別預先定義的順序中的資料表中的所有記錄的欄位所組成。 索引欄位必須是唯一的因為索引物件的唯一屬性也會設為**TRUE**在 DAO 中。 如果主索引鍵是由多個欄位所組成，每個欄位可以包含重複的值，但每個索引的所有欄位的值組合必須是唯一。 主索引鍵資料表的索引鍵所組成，並通常包含主索引鍵相同的欄位。  
  
 當您設定資料表的主索引鍵時，主索引鍵會自動定義為資料表的主索引。 如需詳細資訊，請參閱 「 主要屬性 」 和 DAO [說明] 中的 < 唯一屬性 > 主題。  
  
> [!NOTE]
>  有，最多可達，一個資料表上的主索引鍵。  
  
 *m_bUnique*  
 指出索引物件是否代表資料表的唯一索引。 如果這個屬性是**TRUE**，索引物件都代表唯一的索引。 以邏輯方式排列唯一、 預先定義順序中的資料表中的所有記錄的一個或多個欄位包含非唯一索引。 如果索引包含一個欄位，該欄位中的值必須是唯一的整個資料表。 如果索引是由多個欄位所組成，每個欄位可以包含重複的值，但每個索引的所有欄位的值組合必須是唯一。  
  
 如果索引物件的唯一和主要屬性設定為**TRUE**，索引是唯一和主要： 它會唯一識別預先定義的邏輯順序中的資料表中的所有記錄。 如果主要屬性設定為**FALSE**，索引為次要索引。 次要索引 （索引鍵和非索引鍵） 以邏輯方式排列中預先定義的順序的記錄，而不做為資料表中記錄的識別碼。  
  
 如需詳細資訊，請參閱 「 主要屬性 」 和 DAO [說明] 中的 < 唯一屬性 > 主題。  
  
 *m_bClustered*  
 指出索引物件是否代表資料表的叢集的索引。 如果這個屬性是**TRUE**，index 物件表示非叢集的索引; 否則它並不會。 叢集的索引包含一或多個非索引鍵欄位、 整體而言排列預先定義的順序中的資料表中的所有記錄。 具有叢集索引，資料表中的資料會依其字面儲存在叢集索引所指定的順序。 叢集的索引會提供能夠有效率地存取資料表中的記錄。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 叢集屬性 」。  
  
> [!NOTE]
>  使用 Microsoft Jet 資料庫引擎，因為 Jet database engine 不支援叢集的索引的資料庫，則會忽略 Clustered 屬性。  
  
 *m_bIgnoreNulls*  
 指出是否在其索引欄位中具有 Null 值的記錄的索引項目。 如果這個屬性是**TRUE**，Null 值欄位沒有索引項目。 若要讓搜尋更快的使用欄位的記錄，您可以定義欄位的索引。 如果您允許編製索引的欄位中的 Null 項目，而且預期會有許多 null 項目，您可以設定忽略 Null 屬性索引物件**TRUE**來減少索引所使用的儲存空間量。 忽略 Null 屬性設定和必要的屬性設定一起決定為 Null 的索引值的記錄是否索引項目，如下表所示。  
  
|忽略 Null|必要|中索引欄位為 null|  
|-----------------|--------------|-------------------------|  
|True|False|允許 null 值沒有索引的項目加入。|  
|False|False|允許 null 值加入索引的項目。|  
|True 或 False|True|不允許; null 值沒有索引的項目加入。|  
  
 如需詳細資訊，請參閱本主題說明 DAO 中的 「 忽略 Null 屬性 」。  
  
 `m_bRequired`  
 指出 DAO 索引物件是否需要非 Null 值。 如果這個屬性是**TRUE**，index 物件不允許 Null 值。 如需詳細資訊，請參閱主題 DAO [說明] 中的 < 必要屬性 >。  
  
> [!TIP]
>  當您可以設定此屬性，DAO 索引物件或 field 物件 （包含 tabledef、 資料錄集，或 querydef 物件） 時，則會設定欄位物件。 Field 物件的屬性設定的有效性是之前的索引物件進行檢查。  
  
 *m_bForeign*  
 指出索引物件是否代表資料表中的外部索引鍵。 如果這個屬性是**TRUE**，索引代表資料表中的外部索引鍵。 外部索引鍵是由一或多個外部資料表中唯一識別欄位的主要資料表中的資料列所組成。 Microsoft Jet 資料庫引擎建立外部資料表的索引物件，並設定在外部索引屬性，當您建立的強制執行參考完整性的關聯性。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 外部索引屬性 」。  
  
 *m_lDistinctCount*  
 指出索引物件相關聯的資料表中包含的唯一值數目。 請檢查 DistinctCount 屬性，若要判斷唯一值或中的索引鍵數目。 任何索引鍵是只計算一次，即使該值的多個項目，則可能會索引可讓您重複的值。 這項資訊適用於應用程式嘗試最佳化資料存取，藉由評估索引資訊。 唯一值的數目就是所謂的索引物件的基數。 DistinctCount 屬性會永遠反映實際數目的索引鍵，以在特定時間。 例如，交易回復所造成的變更將不會立即反映在 [DistinctCount] 屬性。 如需詳細資訊，請參閱主題 DAO [說明] 中的 < DistinctCount 屬性 >。  
  
## <a name="remarks"></a>備註  
 參考主要、 次要資料庫，且所有上述表示所傳回的資訊是如何`GetIndexInfo`類別中的成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 不會由 MFC 類別表示索引物件。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或者您可以存取它們全部與`CDaoIndexInfo`藉由呼叫物件`GetIndexInfo`包含物件的成員函式。  
  
 `CDaoIndexInfo` 有一個建構函式和解構函式，才能正確地配置和解除配置中的索引欄位資訊`m_pFieldInfos`。  
  
 所擷取的資訊`GetIndexInfo`tabledef 物件成員函式會儲存在`CDaoIndexInfo`結構。 呼叫`GetIndexInfo`包含 tabledef 物件的索引集合中儲存的索引物件的成員函式。 `CDaoIndexInfo` 也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoIndexInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)

