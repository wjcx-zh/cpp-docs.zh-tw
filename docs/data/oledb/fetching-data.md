---
title: "擷取資料 | Microsoft Docs"
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
  - "資料 [C++], 擷取"
  - "擷取"
  - "OLE DB 消費者樣板 [C++], 擷取資料"
  - "資料列集 [C++], 擷取"
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 擷取資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以在開啟資料來源、工作階段和資料列集物件之後擷取資料。  根據所使用的存取子型別而定，您可能需要繫結資料行。  
  
### 若要擷取資料  
  
1.  使用適當的 \[開啟\] 命令開啟資料列集。  
  
2.  如果您正在使用 `CManualAccessor`，請繫結輸出資料行 \(如果您還沒完成這個動作\)。  若要繫結資料行，請呼叫 `GetColumnInfo`，然後按照下列範例所示，以繫結建立存取子：  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  撰寫一個 `while` 迴圈以擷取資料。  依照下列範例所示，在這個迴圈中呼叫 `MoveNext`，將游標往前移，並測試傳回值是否為 S\_OK：  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  您可以在這個 `while` 迴圈內，根據您的存取子型別擷取資料。  
  
    -   如果您使用的是 [CAccessor](../../data/oledb/caccessor-class.md) 類別，您應該有包含資料成員的使用者資料錄。  依照下列範例所示，使用那些資料成員存取資料：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   如果使用的是 `CDynamicAccessor` 或 `CDynamicParameterAccessor` 類別，您可以依照下列範例所示，使用 `GetValue` 和 `GetColumn` 存取函式以擷取資料。  如果您要決定您正在使用的資料型別，請使用 `GetType`。  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   如果使用的是 `CManualAccessor` ，就必須依照下列範例所示，指定擁有的資料成員並繫結它們，然後再直接進行存取：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## 請參閱  
 [使用 OLE DB 消費者樣板](../../data/oledb/working-with-ole-db-consumer-templates.md)