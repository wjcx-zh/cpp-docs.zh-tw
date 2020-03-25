---
title: 未使用精靈建立消費者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: fff4146681e31f0f1fea9fbaa559de7c722740d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211454"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>未使用精靈建立消費者

下列範例假設您要將 OLE DB 消費者支援新增至現有的 ATL 專案。 如果您想要將 OLE DB 消費者支援新增至 MFC 應用程式，您應該執行 **MFC 應用程式精靈**，這會建立所需的所有支援，並叫用執行應用程式所需的 MFC 常式。

若要在不使用 **ATL OLE DB 消費者精靈**的情況下新增 OLE DB 消費者支援：

- 在您的*pch .h*檔案中，附加下列 `#include` 語句：

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

消費者通常會以程式設計的方式執行下列一連串作業：

1. 建立將資料行繫結至區域變數的使用者記錄類別。 在此範例中，`CMyTableNameAccessor` 是使用者記錄類別 (請參閱[使用者記錄](../../data/oledb/user-records.md))。 此類別包含資料行對應及參數對應。 在使用者記錄類別中，針對您在資料行對應中指定的每個欄位，宣告資料成員；並針對這些每個資料成員，宣告狀態資料成員和長度資料成員。 如需詳細資訊，請參閱[在精靈產生的存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

    > [!NOTE]
    > 如果您撰寫自己的消費者，資料變數必須出現在狀態和長度變數之前。

- 具現化資料來源和工作階段。 決定要使用的存取子和資料列集類型，然後使用 [CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md) 具現化資料列集:

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- 呼叫 `CoInitialize` 以初始化 COM。 這是在主要程式碼中呼叫的。 例如：

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- 呼叫 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 或其中一個變化。

- 開啟資料來源的連線、開啟工作階段，以及開啟並初始化資料列集 (如果是命令，也執行它)：

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- 選擇性地使用 `CDBPropSet::AddProperty` 設定資料列集屬性，並將其當作參數，傳遞到 `rs.Open`。 如需如何完成此操作的範例，請參閱`GetRowsetProperties`消費者精靈產生的方法[中的 ](../../data/oledb/consumer-wizard-generated-methods.md)。

- 您現在可以使用資料列集擷取/操作資料。

- 當您的應用程式完成時，請關閉連線、工作階段，以及資料列集：

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   如果您要使用命令，您可能想要在 `ReleaseCommand` 之後呼叫 `Close`。 [CCommand::Close](../../data/oledb/ccommand-close.md) 中的程式碼範例會示範如何呼叫 `Close` 和 `ReleaseCommand`。

- 呼叫 `CoUnInitialize` 以解除初始化 COM。 這是在主要程式碼中呼叫的。

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>另請參閱

[建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)
