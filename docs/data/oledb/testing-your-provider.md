---
title: 測試提供者
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 722757b93d3423b02340c382b16e08a31626bc01
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311939"
---
# <a name="testing-your-provider"></a>測試提供者

在您釋放提供者之前，您應依照指示的循序執行下列測試。 這些測試會顯示提供者對大部分潛在使用者的功能正常。

1. 使用以 OLE DB 取用者範本撰寫的取用[者](../../data/oledb/creating-an-ole-db-consumer.md)應用程式來測試提供者。 測試取用者應涵蓋提供者的所有功能區域（您已新增或修改的所有程式碼）。

1. 使用以 ADO 撰寫的取用者應用程式來測試提供者。 大部分的開發人員（特別是 Microsoft C# Visual Basic 和 microsoft 開發人員）都會針對取用者應用程式使用 ADO 或 ADO.NET。 測試取用者應涵蓋提供者的所有功能區域。 如需 ADO 取用者應用程式的範例，請參閱[Microsoft Visual Basic 中的 ado 程式碼範例](/previous-versions/ms807514(v=msdn.10))。

1. 執行 OLE DB 一致性測試（包括 ADO 一致性測試），以顯示您的提供者符合 OLE DB 提供者的層級0標準。 （如需層級0的說明，請在 OLE DB 程式設計[人員指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)中搜尋**OLE DB 層級0一致性測試**。 這些測試和相關檔會隨附在資料C++存取 SDK 的 Visual 中。 這些測試也有助於顯示，您的提供者會在由其他[服務提供者](../../data/oledb/ole-db-resource-pooling-and-services.md)匯總時順利執行，而且在您修改或加入屬性時特別有用。 如需有關一致性測試的詳細資訊，請參閱資料存取 SDK 的讀我檔案，此檔案位於其中一個 Visual Studio Cd 上。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)