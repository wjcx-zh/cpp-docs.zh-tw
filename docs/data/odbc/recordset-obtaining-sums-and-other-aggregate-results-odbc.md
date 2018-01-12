---
title: "資料錄集： 取得 Sum 和其他彙總結果 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4753193789c95b726a8770cef9a153b041fa762c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>資料錄集：取得 SUM 和其他彙總結果 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明如何取得彙總結果，使用下列[SQL](../../data/odbc/sql.md)關鍵字：  
  
-   **SUM**數值資料類型與計算資料行中值的總計。  
  
-   **MIN**擷取資料行中的最小值與數值資料類型。  
  
-   **最大**具有數值資料類型中擷取資料行中的最大值。  
  
-   **AVG**數值資料類型與計算資料行中的所有值的平均值。  
  
-   **計數**計算任何資料類型的資料行中的記錄數目。  
  
 若要取得統計資料來源中的記錄資訊而非從資料來源擷取記錄，您可以使用這些 SQL 函式。 資料錄集，通常會建立包含單一記錄 （如果所有資料行彙總） 包含的值。 (可能有多個記錄如果您使用**GROUP BY**子句。)這個值會計算或執行 SQL 函式的結果。  
  
> [!TIP]
>  若要加入 SQL **GROUP BY**子句 (且可能**HAVING**子句) 到您的 SQL 陳述式，將它附加至結尾**m_strFilter**。 例如:   
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 您可以限制您使用的篩選和排序資料行取得彙總結果的記錄數目。  
  
> [!CAUTION]
>  有些彙總運算子會傳回不同的資料類型，從彙總的資料行。  
  
-   **SUM**和**AVG**可能會傳回下一個較大的資料類型 (例如，使用呼叫`int`傳回**長**或**雙**)。  
  
-   **計數**通常傳回**長**無論目標資料行類型。  
  
-   **最大**和**MIN**傳回相同的資料類型，這些計算的資料行。  
  
     例如，**加入類別**精靈會建立`long``m_lSales`適應 Sales 資料行，但您必須更換這與`double m_dblSumSales`資料成員，才能容納彙總結果。 請參閱下列範例。  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>若要取得資料錄集的彙總結果  
  
1.  中所述，建立資料錄集[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)包含您要取得彙總結果的資料行。  
  
2.  修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)資料錄集的函式。 取代字串，代表資料行名稱 (第二個引數的[RFX](../../data/odbc/record-field-exchange-using-rfx.md)函式呼叫) 的字串，表示資料行上的彙總函式。 例如，取代：  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     使用：  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  開啟資料錄集。 彙總運算的結果會留在`m_dblSumSales`。  
  
> [!NOTE]
>  精靈會實際指派沒有匈牙利前置詞的資料成員名稱。 例如，精靈會產生`m_Sales`Sales 資料行，而非`m_lSales`先前用於圖例名稱。  
  
 如果您使用[CRecordView](../../mfc/reference/crecordview-class.md)類別，即可檢視資料，您必須變更 DDX 函式呼叫，以顯示新的資料成員值; 在此情況下，將它從變更：  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 收件者:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)