---
title: 實作簡單消費者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 67bce55a19a2aaaf3a8cbb62d7db228513e93c91
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707538"
---
# <a name="implementing-a-simple-consumer"></a>實作簡單消費者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="<=vs-2017"

下列主題示範如何編輯 **MFC 應用程式精靈**和 **ATL OLE DB 消費者精靈**所建立的檔案，來建立簡單消費者。 這個範例包含下列部分：

- [使用消費者擷取資料](#retrieve)示範如何實作消費者中的程式碼，以從資料庫資料表中循列讀取所有資料。

- [為消費者加入書籤支援](#bookmark)示範如何為消費者加入書籤支援。

> [!NOTE]
> 您可以使用本節所述的消費者應用程式來測試 `MyProv` 和 `Provider` 範例提供者。

> [!NOTE]
> 若要建置消費者應用程式來測試 `MyProv` ([增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)中所述的同一個提供者)，您必須包含書籤支援，如[為消費者加入書籤支援](#bookmark)中所述。

## <a name="retrieve" ></a> 使用消費者擷取資料

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>修改主控台應用程式以使用 OLE DB 消費者

1. 在 `MyCons.cpp` 中，插入如下的粗體文字來變更主要程式碼：

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "stdafx.h"
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="bookmark" ></a> 為消費者加入書籤支援

書籤是可在資料表中唯一識別資料列的資料行。 它通常是索引鍵資料行，但並非總是如此；它是提供者專用的。 本節示範如何加入書籤支援。 若要這樣做，您需要在使用者記錄類別中執行下列步驟：

- 將書籤具現化。 這些是型別為 [CBookmark](../../data/oledb/cbookmark-class.md) 的物件。

- 透過設定 `DBPROP_IRowsetLocate` 屬性來向提供者要求書籤資料行。

- 使用 [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) 巨集，即可將書籤項目加入至資料行對應。

先前的步驟會為您提供書籤支援，以及要一同運作的書籤物件。 此程式碼範例示範一個書籤，如下所示：

- 開啟檔案以供寫入。

- 循列將資料列集資料輸出到檔案。

- 透過呼叫 [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)來將資料列集資料指標移至書籤。

- 輸出已標記為書籤的資料列，並將它附加到檔案結尾。

> [!NOTE]
> 如果您使用此消費者應用程式來測試 `Provider` 範例提供者應用程式，請保留本節所述的書籤支援。

### <a name="to-instantiate-the-bookmark"></a>將書籤具現化

1. 存取子必須保存型別為 [CBookmark](../../data/oledb/cbookmark-class.md) 的物件。 *nSize* 參數會以位元組為單位來指定書籤緩衝區的大小 (通常會針對 32 位元平台指定 4，以及針對 64 位元平台指定 8)。 將下列宣告加入至使用者記錄類別中的資料行資料成員：

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>向提供者要求書籤資料行

1. 在使用者記錄類別的 `GetRowsetProperties` 方法中加入下列程式碼：

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>將書籤項目加入至資料行對應

1. 將下列項目加入至使用者記錄類別中的資料行對應：

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>在主要程式碼中使用書籤

1. 在來自您先前建立之主控台應用程式的 `MyCons.cpp` 檔案中，變更要讀取的主要程式碼，如下所示。 為了使用書籤，主要程式碼需要將自己的書籤物件具現化 (`myBookmark`)；這個書籤與存取子中的書籤 (`m_bookmark`) 不同。

    ```cpp
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
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
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

如需書籤的詳細資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。 [更新資料列集](../../data/oledb/updating-rowsets.md)中也會顯示書籤範例。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
