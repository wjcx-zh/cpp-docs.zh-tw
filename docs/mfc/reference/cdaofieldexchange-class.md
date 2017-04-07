---
title: "CDaoFieldExchange 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- field exchange
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- field exchange, record for DAO classes
- exchanging data between databases and recordsets
- DFX (DAO record field exchange), DAO Record Field Exchange
- RFX (record field exchange)
- CDaoFieldExchange class
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 23
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 31b7121f8e93f85ed73b5d095ac0995f3ddee721
ms.lasthandoff: 02/24/2017

---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 類別
支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|如果目前的作業為非零傳回適用於更新之欄位的類型。|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|指定資料錄集資料成員的型別 — 資料行或參數-由 DFX 函式的所有後續呼叫，直到下次呼叫`SetFieldType`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|DFX 作業正在執行的資料錄集的目前呼叫`DoFieldExchange`成員函式。|  
|[CDaoFieldExchange::m_prs](#m_prs)|資料錄集的 DFX 作業正在執行指標。|  
  
## <a name="remarks"></a>備註  
 `CDaoFieldExchange`沒有基底類別。  
  
 使用這個類別，如果您要撰寫資料交換常式的自訂資料型別。否則，您不會直接使用這個類別。 DFX 之間交換資料的欄位資料成員您[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件和目前的記錄資料來源上的對應的欄位。 DFX 管理這兩個方向，exchange 資料來源和資料來源。 請參閱[技術附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)撰寫自訂 DFX 常式相關資訊。  
  
> [!NOTE]
>  DAO 資料庫類別所基礎開放式資料庫連接 (ODBC) 之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更有能力比 ODBC 架構的 MFC 類別。 DAO 架構類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 它們也支援資料定義語言 (DDL) 作業，例如加入資料表，而不必自行呼叫 DAO 類別。  
  
> [!NOTE]
>  DAO 資料錄欄位交換 (DFX) 是非常類似於 ODBC 架構的 MFC 資料庫類別中的資料錄欄位交換 (RFX) ( `CDatabase`， `CRecordset`)。 如果您了解 RFX，您會發現您輕鬆使用 DFX。  
  
 A`CDaoFieldExchange`物件提供內容資訊所需 dao 資料錄欄位交換生效。 `CDaoFieldExchange`物件支援作業，包括繫結參數和欄位資料成員和設定各種旗標的目前記錄的欄位的數目。 DFX 作業上所定義類型的資料錄集類別資料成員`enum` **FieldType**中`CDaoFieldExchange`。 可能**FieldType**的值為︰  
  
- **CDaoFieldExchange::outputColumn**欄位資料成員。  
  
- **CDaoFieldExchange::param**參數資料成員。  
  
 [IsValidOperation](#isvalidoperation)撰寫您自己的自訂 DFX 常式提供成員函式。 您將使用[SetFieldType](#setfieldtype)經常在您[CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函式。 如需 DFX 全域函式的詳細資訊，請參閱[資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。 撰寫自訂 DFX 常式資料類型的相關資訊，請參閱[技術附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation  
 如果您撰寫您自己的 DFX 函式，呼叫`IsValidOperation`來判斷是否可以在特定欄位資料成員型別上執行目前的操作函式的開頭 ( **CDaoFieldExchange::outputColumn**或**CDaoFieldExchange::param**)。  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的作業適用於更新之欄位的類型為非零。  
  
### <a name="remarks"></a>備註  
 某些 DFX 機制所執行的作業僅適用於其中一個可能的欄位型別。 遵循現有的 DFX 函式的模型。  
  
 如需有關如何撰寫自訂 DFX 常式的詳細資訊，請參閱[技術附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
##  <a name="m_noperation"></a>CDaoFieldExchange::m_nOperation  
 識別要執行的作業[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)欄位 exchange 物件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 `CDaoFieldExchange`物件可提供許多不同的資料錄集的 DFX 作業的內容。  
  
> [!NOTE]
>  **PSEUDONULL** MarkForAddNew 和 SetFieldNull 以下的作業所述的值是用來標記 Null 的欄位的值。 DAO 資料錄欄位交換 (DFX) 機制會使用此值來判斷哪些欄位已被明確標記為 Null。 **PSEUDONULL**不需要[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)欄位。  
  
 可能的值**m_nOperation**是︰  
  
|作業|描述|  
|---------------|-----------------|  
|**AddToParameterList**|建置**參數**子句的 SQL 陳述式。|  
|**AddToSelectList**|建置**選取**子句的 SQL 陳述式。|  
|**BindField**|將資料庫中的欄位繫結至應用程式中的記憶體位置。|  
|**BindParam**|設定資料錄集的查詢參數值。|  
|**修復**|設定 Null 狀態欄位。|  
|**AllocCache**|會配置用來檢查 「 不正常 」 中的欄位資料錄集的快取。|  
|**StoreField**|將目前的記錄儲存至快取。|  
|**LoadField**|還原資料錄集中的快取的資料成員變數。|  
|**FreeCache**|釋出用來檢查 「 不正常 」 中的欄位資料錄集的快取。|  
|`SetFieldNull`|欄位的狀態設定為 Null，而且值**PSEUDONULL**。|  
|**MarkForAddNew**|如果不是標示的欄位是 「 不正常 」 **PSEUDONULL**。|  
|**MarkForEdit**|標示的欄位 「 不正常 」，如果不符合快取。|  
|**SetDirtyField**|設定欄位值標示為 「 不正常 」。|  
|**DumpField**|傾印欄位的內容 （只用於偵錯）。|  
|**MaxDFXOperation**|用於輸入檢查。|  
  
##  <a name="m_prs"></a>CDaoFieldExchange::m_prs  
 包含一個指向[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件相關聯`CDaoFieldExchange`物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType  
 呼叫`SetFieldType`中您`CDaoRecordset`類別的`DoFieldExchange`覆寫。  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>參數  
 `nFieldType`  
 值為**列舉 FieldType**中宣告`CDaoFieldExchange`，這可以是下列其中一項︰  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>備註  
 通常，類別會為您撰寫此呼叫。 如果您撰寫自己的函式，並使用精靈寫入您`DoFieldExchange`函式，將呼叫加入至您自己的函式外部的欄位對應。 如果您不使用精靈，將不會有欄位對應。 在呼叫之前呼叫 DFX 函式，一個用於您的類別中的每個欄位資料成員，並且會識別欄位型別為**CDaoFieldExchange::outputColumn**。  
  
 如果您將參數化資料錄集類別，您應該加入 DFX 呼叫 （在欄位對應的） 之外的所有參數資料成員，且在完成呼叫這些呼叫`SetFieldType`。 將值傳遞**CDaoFieldExchange::param**。 (相反地，您可以使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和設定其參數值。)  
  
 一般情況下，每個群組的欄位資料成員或參數資料成員相關聯的 DFX 函式呼叫必須加上呼叫`SetFieldType`。 `nFieldType`每個參數`SetFieldType`呼叫識別遵循 DFX 函式呼叫所代表的資料成員的型別`SetFieldType`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)

