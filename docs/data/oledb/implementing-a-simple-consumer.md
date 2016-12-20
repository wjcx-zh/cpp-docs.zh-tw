---
title: "實作簡單消費者 | Microsoft Docs"
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
  - "用戶端, 建立"
  - "OLE DB 消費者, 實作"
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實作簡單消費者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列主題顯示如何編輯 MFC 應用程式精靈和 ATL OLE DB 消費者精靈所建立的檔案，以建立簡單消費者。  此範例具有下列幾個部分：  
  
-   「以消費者擷取資料」顯示如何在消費者內實作可從資料庫資料表內逐一資料列地讀取所有資料的程式碼。  
  
-   「加入書籤支援至消費者」顯示如何將書籤支援加至消費者。  
  
-   「加入 XML 支援至消費者」顯示如何修改消費者程式碼，以便將擷取到的資料列集資料輸出成 XML 資料。  
  
> [!NOTE]
>  您可使用本章節所說明的消費者應用程式，進行測試 MyProv 和 Provider 範例提供者。  
  
> [!NOTE]
>  若要建置一個消費者應用程式來測試 MyProv \([增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)所描述的同一個提供者\)，您必須包含書籤支援，如同「加入書籤支援至消費者」所述。  
  
> [!NOTE]
>  若要建置一個消費者應用程式來測試提供者，請省略「加入書籤支援至消費者」內所述的書籤支援，並跳到「加入 XML 支援至消費者」。  
  
## 以消費者擷取資料  
  
#### 若要修改主控台應用程式來使用 OLE DB 消費者  
  
1.  在 MyCons.cpp 中插入粗體文字來變更主程式碼，如下所示：  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);        // Instantiate rowset    CProducts rs;        hr = rs.OpenAll();    ATLASSERT( SUCCEEDED( hr ) );    hr = rs.MoveFirst();        // Iterate through the rowset    while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )    {       // Print out the column information for each row       printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",              rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );       hr = rs.MoveNext();    }        rs.Close();    rs.ReleaseCommand();        CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## 加入書籤支援至消費者  
 書籤是可唯一識別資料表內資料列的資料行。  一般而言它是索引鍵資料行，但不一定全是；這是由提供者所決定。  這個章節將教您如何加入書籤支援。  若要進行這項作業，您需要在使用者資料錄類別內進行下列步驟：  
  
-   產生書籤。  這些為型別 [CBookmark](../../data/oledb/cbookmark-class.md) 的物件。  
  
-   透過設定 **DBPROP\_IRowsetLocate** 屬性來向提供者要求書籤資料行。  
  
-   使用 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md) 巨集將書籤項目加入至資料行對應。  
  
 上述步驟提供您書籤支援以及可用來工作的書籤物件。  這個程式碼範例會展示書籤，如下所示：  
  
-   開啟一個可供寫入的檔案。  
  
-   將資料列集資料逐一資料列地輸出至檔案。  
  
-   透過呼叫 [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md) 將資料列集游標移至書籤。  
  
-   輸出加入書籤的資料列，將它附加至檔案最後。  
  
> [!NOTE]
>  若您使用這個消費者應用程式來測試 Provider 範例提供者應用程式，請省略本章節所說明的書籤支援。  
  
#### 若要將書籤執行個體化  
  
1.  存取子需要包含一型別為 [CBookmark](../../data/oledb/cbookmark-class.md) 的物件。  `nSize` 參數指定書籤緩衝區的大小，以位元組為單位 \(一般而言對於 32 位元平台為 4，64 位元平台為 8\)。  將下列宣告加至使用者資料錄類別內的資料行資料成員之中：  
  
    ```  
    //////////////////////////////////////////////////////////////////////  
    // Products.h  
    class CProductsAccessor  
    {  
    public:  
       CBookmark<4> m_bookmark;   // Add bookmark declaration  
       LONG m_ProductID;  
       ...  
    ```  
  
#### 若要向提供者要求書籤資料行  
  
1.  將下列程式碼加入使用者資料錄類別內的 `GetRowsetProperties` 方法之中：  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks    pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### 若要將書籤項目加入資料行對應內  
  
1.  將下列項目加入使用者資料錄類別內的資料行對應之中：  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### 若要在您的主程式碼內使用書籤  
  
1.  在先前建立的主控台應用程式的 MyCons.cpp 檔內，將主程式碼作如下變更。  若要使用書籤，主程式碼需要執行個體化自己的書籤物件 \(`myBookmark`\)，這和存取子 \(`m_bookmark`\) 內的書籤是不同的書籤。  
  
    ```  
    ///////////////////////////////////////////////////////////////////////  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
  
    #include "stdafx.h"  
    #include "Products.h"   
    #include <iostream>  
    #include <fstream>  
    using namespace std;  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);  
  
       // Instantiate rowset  
       CProducts rs;  
  
       hr = rs.OpenAll();  
       hr = rs.MoveFirst();  
  
       // Cast CURRENCY m_UnitPrice to a long value  
       LONGLONG lPrice = rs.m_UnitPrice.int64;  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // Instantiate a bookmark object myBookmark for the main code  
       CBookmark<4> myBookmark;  
       int nCounter = 0;  
  
       // Iterate through the rowset and output column data to output.txt row by row  
       // In the file, mark the beginning of this set of data:  
       outfile << "initial row dump" << endl;  
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          nCounter++;  
          if( nCounter == 5 )  
             myBookmark = rs.bookmark;  
          // Output the column information for each row:  
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;  
          hr = rs.MoveNext();  
       }  
  
       // Move cursor to bookmark  
       hr = rs.MoveToBookmark(myBookmark);  
  
       // Iterate through the rowset and output column data to output.txt row by row  
       // In the file, mark the beginning of this set of data:  
       outfile << "row dump starting from bookmarked row" << endl;  
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          // Output the column information for each row  
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;  
          hr = rs.MoveNext();  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
 如需書籤的詳細資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  書籤的範例也顯示在[更新資料列集](../../data/oledb/updating-rowsets.md)。  
  
## 加入 XML 支援至消費者  
 如同[存取 XML 資料](../../data/oledb/accessing-xml-data.md)中所討論，有兩個方法可從資料來源中擷取 XML 資料：使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 或使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  這個範例使用 `CStreamRowset`，此法較有效率，但是在執行此範例應用程式的電腦上需要執行 SQL Server 2000。  
  
#### 若要修改命令類別以繼承自 CStreamRowset  
  
1.  在您先前建立的消費者應用程式內，變更 `CCommand` 宣告來將 `CStreamRowset` 指定成資料列集類別，如下所示：  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### 若要修改主程式碼來擷取和輸出 XML 資料  
  
1.  在先前建立的主控台應用程式的 MyCons.cpp 檔內，將主程式碼變更如下：  
  
    ```  
    ///////////////////////////////////////////////////////////////////////  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
  
    #include "stdafx.h"  
    #include "Products.h"   
    #include <iostream>  
    #include <fstream>  
    using namespace std;  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);  
  
       // Instantiate rowset  
       CProducts rs;  
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
          HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## 請參閱  
 [使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)