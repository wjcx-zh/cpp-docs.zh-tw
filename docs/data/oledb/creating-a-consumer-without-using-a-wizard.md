---
title: "不使用精靈建立消費者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a61de0a4621f6f9387da23093f9f450749129ac3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>未使用精靈建立消費者
下列範例假設您要加入至現有的 ATL 專案 OLE DB 取用者支援。 如果您想要將 OLE DB 取用者支援加入至 MFC 應用程式，您應該執行 MFC 應用程式精靈，以建立所有支援的必要和 MFC 常式所需執行應用程式會叫用。  
  
 若要新增 OLE DB 取用者支援，而不使用 ATL OLE DB 消費者精靈：  
  
-   在 Stdafx.h 檔案中，附加下列`#include`陳述式：  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 以程式設計的方式，取用者通常會執行下列一系列的作業：  
  
-   建立繫結至區域變數的資料行的使用者記錄類別。 在此範例中，`CMyTableNameAccessor`是使用者記錄類別 (請參閱[使用者資料錄](../../data/oledb/user-records.md))。 這個類別包含的資料行對應和參數對應。 宣告在您指定資料行對應; 中的每個欄位的使用者記錄類別中的資料成員針對每個這些資料成員，同時宣告狀態資料成員和長度資料成員。 如需詳細資訊，請參閱[精靈產生的存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。  
  
    > [!NOTE]
    >  如果您撰寫自己的消費者，資料變數必須出現在狀態和長度變數之前。  
  
-   具現化的資料來源和工作階段。 決定何種存取子和資料列集使用，然後再具現化資料列集使用[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
-   呼叫**CoInitialize**初始化 com。 這通常稱為主要的程式碼中。 例如:   
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   呼叫[cdatasource:: Open](../../data/oledb/cdatasource-open.md)或其中一個其變化。  
  
-   開啟資料來源的連接、 開啟工作階段，然後開啟初始化資料列集 （並命令也執行）：  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   （選擇性） 設定資料列集屬性使用`CDBPropSet::AddProperty`並將其傳遞為參數，以`rs.Open`。 如需執行方式的範例，請參閱中的 GetRowsetProperties[消費者精靈產生方法](../../data/oledb/consumer-wizard-generated-methods.md)。  
  
-   您現在可以使用資料列集來擷取/處理資料。  
  
-   完成您的應用程式時，請關閉連線、 session 和資料列集：  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     如果您使用命令時，您可能想要呼叫`ReleaseCommand`之後**關閉**。 中的程式碼範例[ccommand:: Close](../../data/oledb/ccommand-close.md)示範如何呼叫**關閉**和`ReleaseCommand`。  
  
-   呼叫**CoUnInitialize**停止初始化 com。 這通常稱為主要的程式碼中。  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>請參閱  
 [建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)