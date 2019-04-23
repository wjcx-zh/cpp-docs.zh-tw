---
title: 未使用精靈建立消費者
ms.date: 10/12/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 029fe6866df81d366cc3bc15096f638791faa413
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030416"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>未使用精靈建立消費者

下列範例假設您將 OLE DB 取用者支援新增至現有的 ATL 專案。 如果您想要將 OLE DB 取用者的支援新增至 MFC 應用程式，您應該執行**MFC 應用程式精靈**，這會建立所需的所有支援，並叫用 MFC 執行的應用程式時所需的常式。

若要加入 OLE DB 取用者的支援，而不使用**ATL OLE DB 消費者精靈**:

- 在 pch.h 檔案中，附加下列`#include`陳述式：

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

以程式設計的方式，取用者通常會執行下列一連串作業：

1. 建立繫結至區域變數的資料行的使用者記錄類別。 在此範例中，`CMyTableNameAccessor`是使用者記錄類別 (請參閱 <<c2> [ 筆使用者記錄](../../data/oledb/user-records.md))。 這個類別包含的資料行對應及參數對應。 宣告使用者記錄類別，針對您指定資料行對應; 中每個欄位中的資料成員針對每個這些資料成員，也宣告的狀態資料成員和長度資料成員。 如需詳細資訊，請參閱 <<c0> [ 精靈產生存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

    > [!NOTE]
    > 如果您撰寫自己的消費者，資料變數必須出現之前的狀態和長度的變數。

- 具現化的資料來源和工作階段。 決定何種存取子和資料列集使用，然後具現化資料列集，使用[CCommand](../../data/oledb/ccommand-class.md)或是[CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- 呼叫`CoInitialize`初始化 com。 這稱為主要的程式碼中。 例如: 

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- 呼叫[cdatasource:: Open](../../data/oledb/cdatasource-open.md)或其中一個其變化。

- 開啟資料來源的連接、 開啟工作階段，並開啟和初始化的資料列集 （並如果命令中，也執行）：

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- （選擇性） 設定資料列集屬性使用`CDBPropSet::AddProperty`，並將它們傳遞做為參數`rs.Open`。 如需如何做到這點的範例，請參閱`GetRowsetProperties`中[消費者精靈產生方法](../../data/oledb/consumer-wizard-generated-methods.md)。

- 您現在可以使用資料列集擷取/處理資料。

- 當您的應用程式完成時，請關閉連線、 工作階段，以及資料列集：

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   如果您使用的命令，您可能想要呼叫`ReleaseCommand`之後`Close`。 中的程式碼範例[ccommand:: Close](../../data/oledb/ccommand-close.md)示範如何呼叫`Close`和`ReleaseCommand`。

- 呼叫`CoUnInitialize`解除初始化 com。 這稱為主要的程式碼中。

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>另請參閱

[建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)