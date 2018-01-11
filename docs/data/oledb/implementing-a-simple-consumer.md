---
title: "實作簡單消費者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 43ebcd38a3125db7373755b1ebf5366cae8af56b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-simple-consumer"></a>實作簡單消費者
下列主題示範如何編輯 MFC 應用程式精靈和 ATL OLE DB 消費者精靈 建立簡單消費者所建立的檔案。 這個範例包含下列部分：  
  
-   在 「 擷取資料取用者使用 「 示範如何讀取所有資料列，從資料庫資料表的取用者中實作程式碼。  
  
-   「 加入書籤支援取用者 」 會示範如何加入書籤支援給取用者。  
  
-   「 將 XML 支援加入至取用者 」 會顯示如何修改輸出所擷取的資料列集的資料為 XML 資料的取用者程式碼。  
  
> [!NOTE]
>  您可以使用本節中所述的取用者應用程式來測試 MyProv 和提供者範例提供者。  
  
> [!NOTE]
>  若要建立取用者應用程式來測試 MyProv (相同的提供者中所述[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md))，「 加入書籤支援至取用者。 」 中所述，您必須包含書籤支援  
  
> [!NOTE]
>  若要建置測試提供者取用者應用程式，讓 「 加入書籤支援至消費者 」 中所述的書籤支援並跳到 < 加入 XML 給取用者的支援 >。  
  
## <a name="retrieving-data-with-the-consumer"></a>取用者以擷取資料  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>若要修改的主控台應用程式，以使用 OLE DB 消費者  
  
1.  在 MyCons.cpp，變更主要的程式碼插入粗體文字，如下所示：  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset   CProducts rs;   hr = rs.OpenAll();   ATLASSERT( SUCCEEDED( hr ) );   hr = rs.MoveFirst();   // Iterate through the rowset   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row      printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",             rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );      hr = rs.MoveNext();   }   rs.Close();   rs.ReleaseCommand();   CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="adding-bookmark-support-to-the-consumer"></a>取用者来加入書籤支援  
 書籤是唯一識別資料表中的資料列的資料行。 通常它是索引鍵資料行，但不是一定。它是特定提供者。 本節說明如何加入書籤支援。 若要這樣做，您需要執行下列動作，使用者記錄類別中：  
  
-   具現化這些書籤。 這些都是物件的型別[CBookmark](../../data/oledb/cbookmark-class.md)。  
  
-   藉由設定要求的書籤資料行從提供者**DBPROP_IRowsetLocate**屬性。  
  
-   使用將書籤項目加入至資料行對應[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)巨集。  
  
 先前的步驟會提供書籤支援和書籤物件來進行工作。 這個程式碼範例將示範一個書籤，如下所示：  
  
-   開啟檔案進行寫入。  
  
-   輸出檔的資料列集資料列。  
  
-   將資料列集資料指標移至書籤，藉由呼叫[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)。  
  
-   輸出已標記書籤的資料列，並將它附加至檔案結尾。  
  
> [!NOTE]
>  如果您使用此取用者應用程式來測試提供者範例提供者應用程式時，將這一節所述的書籤支援。  
  
#### <a name="to-instantiate-the-bookmark"></a>具現化書籤  
  
1.  存取子必須包含型別的物件[CBookmark](../../data/oledb/cbookmark-class.md)。 `nSize`參數指定書籤緩衝區的大小，以位元組為單位 (通常為 32 位元平台 4) 和 64 位元平台為 8。 將下列宣告加入至使用者記錄類別中的資料行資料成員：  
  
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
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>若要從提供者要求的書籤資料行  
  
1.  加入下列程式碼中的`GetRowsetProperties`中使用者記錄類別的方法：  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>將書籤項目加入至資料行對應  
  
1.  將下列項目加入至資料行中的對應使用者記錄類別：  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>若要使用主要程式碼中的書籤  
  
1.  在 MyCons.cpp 檔案從您先前建立的主控台應用程式中，變更主要的程式碼，才能讀取，如下所示。 若要使用書籤，主要的程式碼需要它自己的書籤物件具現化 (`myBookmark`); 這是從存取子中的一個不同的書籤 (`m_bookmark`)。  
  
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
  
 如需書籤的詳細資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。 書籤的範例也會在顯示[更新資料列集](../../data/oledb/updating-rowsets.md)。  
  
## <a name="adding-xml-support-to-the-consumer"></a>將 XML 支援加入至取用者  
 中所述[存取 XML 資料](../../data/oledb/accessing-xml-data.md)，以從資料來源擷取 XML 資料的兩種方式： 使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md)或使用[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。 這個範例會使用`CStreamRowset`，更有效率，但必須要有執行此範例應用程式在電腦上執行的 SQL Server 2000。  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>若要修改繼承自 CStreamRowset 命令類別  
  
1.  在您先前建立取用者應用程式的情況下，變更您`CCommand`宣告指定`CStreamRowset`做為資料列集類別，如下所示：  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>若要修改主要的程式碼，以擷取並輸出 XML 資料  
  
1.  在 MyCons.cpp 檔案從您先前建立的主控台應用程式中，變更主要的程式碼，才能讀取，如下所示：  
  
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
  
## <a name="see-also"></a>請參閱  
 [使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)