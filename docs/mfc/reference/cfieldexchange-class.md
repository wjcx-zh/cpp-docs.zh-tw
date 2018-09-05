---
title: CFieldExchange 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76167793f7252540dbe9feedbb2d83678ebdcacb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688382"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 類別
支援資料庫類別使用的資料錄欄位交換 (RFX) 和大量資料錄欄位交換 (Bulk RFX) 常式。  
  
## <a name="syntax"></a>語法  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|傳回非零值，如果目前的作業是適當的更新之欄位的類型。|  
|[CFieldExchange::SetFieldType](#setfieldtype)|指定資料錄集的資料成員的型別 — 資料行或參數-由所有下列呼叫 RFX 函式，直到下次呼叫`SetFieldType`。|  
  
## <a name="remarks"></a>備註  
 `CFieldExchange` 沒有基底類別。  
  
 使用這個類別，如果您正在撰寫的自訂資料類型，或當您實作大量資料列擷取; 的資料交換常式否則，您不會直接使用這個類別。 RFX 和 Bulk RFX 之間交換資料的資料錄集物件的欄位資料成員和資料來源上目前的記錄之對應欄位。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md)改。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 A`CFieldExchange`物件提供內容資訊所需的資料錄欄位交換 」 或 「 大量資料錄欄位交換才會放置。 `CFieldExchange` 物件支援多個作業，包括繫結參數和欄位資料成員，以及目前的資料錄的欄位上設定各種旗標。 RFX 和 Bulk RFX 作業將會在資料錄集類別的型別所定義的資料成員**enum** **FieldType**在`CFieldExchange`。 可能**FieldType**的值為：  
  
- `CFieldExchange::outputColumn` 欄位資料成員。  
  
- `CFieldExchange::inputParam` 或`CFieldExchange::param`輸入的參數之資料成員。  
  
- `CFieldExchange::outputParam` 輸出參數之資料成員。  
  
- `CFieldExchange::inoutParam` 輸入/輸出參數之資料成員。  
  
 大部分的類別的成員函式和資料成員可供撰寫您自己的自訂 RFX 常式。 您將使用`SetFieldType`常見問題。 如需詳細資訊，請參閱文章[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)並[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 如需大量資料列擷取資訊，請參閱文章[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需 RFX 和 Bulk RFX 全域函式的詳細資訊，請參閱[記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)此參考的 MFC 巨集和全域區段中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CFieldExchange`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdb.h  
  
##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType  
 如果您撰寫您自己的 RFX 函式，呼叫`IsFieldType`在您的函式，以判斷是否可以在特定欄位或參數的資料成員類型上執行目前的操作開頭 ( `CFieldExchange::outputColumn`， `CFieldExchange::inputParam`， `CFieldExchange::param`， `CFieldExchange::outputParam`，或`CFieldExchange::inoutParam`)。  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>參數  
 *pnField*  
 此參數中傳回之欄位或參數的資料成員的序號。 此數字中的資料成員的順序對應[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或是[CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函式。  
  
### <a name="return-value"></a>傳回值  
 如果目前的作業可對目前的欄位或參數類型為非零。  
  
### <a name="remarks"></a>備註  
 請遵循現有的 RFX 函式的模型。  
  
##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType  
 您必須呼叫`SetFieldType`在您的資料錄集類別[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或是[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)覆寫。  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>參數  
 *nFieldType*  
 值為`enum FieldType`中宣告`CFieldExchange`，它可以是下列其中一項：  
  
- `CFieldExchange::outputColumn`  
  
- `CFieldExchange::inputParam`  
  
- `CFieldExchange::param`  
  
- `CFieldExchange::outputParam`  
  
- `CFieldExchange::inoutParam`  
  
### <a name="remarks"></a>備註  
 欄位資料成員，您必須呼叫`SetFieldType`搭配參數`CFieldExchange::outputColumn`，後面接著呼叫 RFX 或 Bulk RFX 函式。 如果您未實作大量資料列擷取，則 ClassWizard 會放置這`SetFieldType`的欄位對應區段，為您呼叫`DoFieldExchange`。  
  
 如果您將參數化資料錄集類別，您必須呼叫`SetFieldType`同樣地，之外任何欄位對應 區段中，後面接著 RFX 呼叫所有參數的資料成員。 每種類型的參數資料成員必須有它自己`SetFieldType`呼叫。 下表可區別不同的值，您可以傳遞給`SetFieldType`來代表您的類別的參數資料成員：  
  
|SetFieldType 參數值|參數的資料成員的型別|  
|----------------------------------|-----------------------------------|  
|`CFieldExchange::inputParam`|輸入的參數。 值，這個值會傳遞至資料錄集的查詢或預存程序。|  
|`CFieldExchange::param` | 與相同`CFieldExchange::inputParam`。|  
|`CFieldExchange::outputParam`|輸出參數。 資料錄集的預存程序的傳回值。|  
|`CFieldExchange::inoutParam`|輸入/輸出參數。 值，這個值會傳遞給方法以及從資料錄集的預存程序傳回。|  
  
 一般情況下，每個群組的欄位資料成員或參數的資料成員相關聯的 RFX 函式呼叫的前面必須有呼叫`SetFieldType`。 *NFieldType*每個參數`SetFieldType`呼叫識別遵循 RFX 函式呼叫所代表的資料成員的型別`SetFieldType`呼叫。  
  
 如需有關如何處理輸出和輸入/輸出參數的詳細資訊，請參閱 <<c0> `CRecordset` 成員函式[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 如需 RFX 和 Bulk RFX 函式的詳細資訊，請參閱主題[記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。 如需大量資料列擷取的相關資訊，請參閱文章[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
 此範例示範數個呼叫 RFX 函式及隨附的呼叫`SetFieldType`。 請注意，`SetFieldType`透過呼叫`pFX`指標`CFieldExchange`物件。  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)
