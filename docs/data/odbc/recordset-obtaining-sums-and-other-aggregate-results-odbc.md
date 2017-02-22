---
title: "資料錄集：取得 SUM 和其他彙總結果 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 擷取 SQL 彙總值"
  - "資料錄集, 擷取 SQL 彙總值"
  - "從資料錄集擷取 SQL 彙總值"
  - "SQL 彙總值"
  - "SQL 彙總值, 從資料錄集擷取"
  - "SQL Server 專案, 從資料錄集擷取彙總值"
  - "SQL, 從資料錄集擷取彙總值"
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄集：取得 SUM 和其他彙總結果 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明如何使用下列 [SQL](../../data/odbc/sql.md) 關鍵字來取得彙總 \(Aggregate\) 結果：  
  
-   **SUM**：計算數字資料型別的資料行內的總值。  
  
-   **MIN**：在數字資料型別的資料行內擷取最小值。  
  
-   **MAX**：在數字資料型別的資料行內擷取最大值。  
  
-   **AVG**：計算數字資料型別的資料行內所有值的平均值。  
  
-   **COUNT**：計算任何資料型別的資料行內的資料錄數目。  
  
 您可以使用這些 SQL 函式，來取得資料來源內資料錄的相關統計資訊，而不需從資料來源擷取資料錄。  建立的資料錄集通常是由包含一個數值的單一資料錄 \(若所有的資料行都是彙總的\) 所組成 \(若您使用 **GROUP BY** 子句，則可能會有一個以上的資料錄\)。此數值是計算或執行 SQL 函式所取得的結果。  
  
> [!TIP]
>  若要加入 SQL **GROUP BY** 子句 \(或者可能是 **HAVING** 子句\) 至您的 SQL 陳述式，請將它附加至 **m\_strFilter** 的結尾。  例如：  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 您可限制所使用的資料錄數目，以篩選條件和排序資料行來取得彙總結果。  
  
> [!CAUTION]
>  某些彙總運算子會傳回與彙總的資料行不同的資料型別。  
  
-   **SUM** 和 **AVG** 可能傳回下一個更大的資料型別 \(例如，呼叫時使用 `int` 卻傳回 **LONG** 或 **double**\)。  
  
-   **COUNT** 通常會傳回 **LONG** 而不管目標資料行的型別。  
  
-   **MAX** 和 **MIN** 會傳回與它們所計算的資料行相同的資料型別。  
  
     例如，**加入類別**精靈會建立 `long` `m_lSales` 供銷售資料行使用，但需要使用 `double m_dblSumSales` 資料成員來取代它，以供彙總結果使用。  請參閱下列範例。  
  
#### 若要取得資料錄集的彙總結果  
  
1.  建立在[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中說明的資料錄集，包含有您想要取得彙總結果的資料行。  
  
2.  修改資料錄集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 函式。  使用代表在資料行上彙總函式的字串，取代代表資料行名稱的字串 \([RFX](../../data/odbc/record-field-exchange-using-rfx.md) 函式呼叫的第二個引數\)。  例如，取代：  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     成為：  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  開啟資料錄集。  彙總作業的結果會保留在 `m_dblSumSales`。  
  
> [!NOTE]
>  精靈會實際指派不含匈牙利前置字元的資料成員名稱。  例如，精靈會產生銷售資料行的 `m_Sales`，而不產生先前範例所使用的 `m_lSales` 名稱。  
  
 如果正在使用 [CRecordView](../../mfc/reference/crecordview-class.md) 類別來檢視資料，您必須將 DDX 函式呼叫變更為顯示新資料成員值，在這個案例中，會從下列程式碼變更：  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 To:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)