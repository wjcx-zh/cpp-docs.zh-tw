---
title: 資料錄欄位交換： RFX 的使用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 296ae2e4f535e08924a77b8726b93778a6da5026
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-using-rfx"></a>資料錄欄位交換：RFX 的使用
本主題說明您如何使用 RFX 相對於架構。  
  
> [!NOTE]
>  本主題適用於衍生自類別[CRecordset](../../mfc/reference/crecordset-class.md)的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 與 RFX 相似。 若要了解的差異，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 下列主題包含相關的資訊：  
  
-   [資料錄欄位交換： 精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)介紹 RFX 的主要元件，並說明的程式碼，MFC 應用程式精靈和**加入類別**(中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 以支援 RFX 和如何您可能想要修改精靈程式碼撰寫。  
  
-   [資料錄欄位交換： RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)說明撰寫呼叫 RFX 函式，在您`DoFieldExchange`覆寫。  
  
 下表顯示您相對於架構會做為您的角色。  
  
### <a name="using-rfx-you-and-the-framework"></a>使用 RFX： 您與架構  
  
|您|架構|  
|---------|-------------------|  

|宣告您的資料錄集類別的精靈。 指定的欄位資料成員的名稱和資料類型。 |精靈衍生`CRecordset`類別和寫入[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)讓您覆寫時，包括 RFX 函式的呼叫，每個欄位資料成員。 |  
|（選擇性）手動新增任何所需的參數資料成員的類別。 手動新增的 RFX 函式呼叫`DoFieldExchange`每個參數資料成員，將呼叫加入[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)群組的參數，並指定參數的總數[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). 請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。 | |  
|（選擇性）以手動方式將額外的資料行繫結至欄位資料成員。 手動遞增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 請參閱[資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。 | |  

|建構資料錄集類別的物件。 之前使用物件，將其參數的值資料成員，如果有的話。 |為了提高效率，架構會 prebinds 參數，使用 ODBC。 當您傳遞參數值時，架構會將它們傳送至資料來源。 參數值傳送的變動，除非已經變更的排序及/或篩選的字串。 |  
|開啟資料錄集物件，使用[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)。 |執行資料錄集的查詢、 將資料行繫結至資料錄集，和呼叫的欄位資料成員`DoFieldExchange`第一個選取的記錄和資料錄集的欄位資料成員之間交換資料。 |  
|捲動資料錄集使用[CRecordset::Move](../../mfc/reference/crecordset-class.md#move)或功能表或工具列命令。 |呼叫`DoFieldExchange`將資料傳送至的欄位資料成員，從新的目前記錄。 |  
|加入、 更新和刪除記錄。 |呼叫`DoFieldExchange`將資料傳送至資料來源。 |  
  
## <a name="see-also"></a>另請參閱  
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [資料錄集： 取得 Sum 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)   
 [巨集、 全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

