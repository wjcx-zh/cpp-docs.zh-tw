---
title: "未使用精靈建立消費者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 消費者, 建立"
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 未使用精靈建立消費者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例假設您要將 OLE DB 消費者支援加入現有 ATL 專案。  如果您要將 OLE DB 消費者支援加入 MFC 應用程式，您應該執行 MFC 應用程式精靈，它會建立所有必要的支援，並叫用 \(Invoke\) 執行該應用程式所需的 MFC 常式。  
  
 若要在未使用 ATL OLE DB 消費者精靈情況下加入 OLE DB 消費者支援：  
  
-   在您的 Stdafx.h 檔內附加下列 `#include` 陳述式 \(Statement\)：  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 就程式設計觀點，消費者通常會執行下列操作順序：  
  
-   建立一個可將資料行繫結至區域變數的使用者資料錄類別。  在這個範例中，`CMyTableNameAccessor` 是使用者資料錄類別 \(請參閱[使用者資料錄](../../data/oledb/user-records.md)\)。  此類別包含資料行對應和參數對應。  在使用者資料錄類別內替您指定於資料行對應內的每個欄位宣告資料成員；針對這些資料成員中的每一項，也宣告一個狀態資料成員和一個長度資料成員。  如需詳細資訊，請參閱[在精靈產生的存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。  
  
    > [!NOTE]
    >  如果您撰寫自己的消費者，資料變數就必須出現在狀態和長度變數之前。  
  
-   執行個體化一個資料來源和一個工作階段。  決定要使用哪種類型的存取子和資料列集，接著對使用 [CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md) 的資料列集執行個體化：  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor> >  
    ```  
  
-   呼叫 **CoInitialize** 以初始化 COM。  這通常呼叫於主程式碼內。  例如：  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   呼叫 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 或其分支之一。  
  
-   開啟一連到資料來源的連接，開啟工作階段，並開啟與初始化資料列集 \(若為命令的話，也請執行它\)：  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   您也可使用 `CDBPropSet::AddProperty` 來設定資料列集屬性，並將它們當做參數傳給 `rs.Open`。  如需如何完成這項作業的範例，請參閱[消費者精靈產生的方法](../../data/oledb/consumer-wizard-generated-methods.md)內的「GetRowsetProperties」。  
  
-   現在您可使用資料列集來擷取\/處理資料。  
  
-   當您的應用程式完成之後，可關閉連接、工作階段和資料列集：  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     若您正在使用一命令，可在 **Close** 之後呼叫 `ReleaseCommand`。  [CCommand::Close](../../data/oledb/ccommand-close.md) 內的程式碼範例顯示如何呼叫 **Close** 和 `ReleaseCommand`。  
  
-   呼叫 **CoUnInitialize** 以取消初始化 COM。  這通常呼叫於主程式碼內。  
  
    ```  
    CoUninitialize();  
    ```  
  
## 請參閱  
 [建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)