---
title: 測試提供者
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: d7a3adad546834e2bdc80a695f4c3bf2259dc0ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038313"
---
# <a name="testing-your-provider"></a>測試提供者

您發行的提供者之前，您應該進行下列測試，顯示的順序。 這些測試顯示，大部分的潛在使用者正確的提供者函式。

1. 測試使用的提供者[消費者](../../data/oledb/creating-an-ole-db-consumer.md)使用 OLE DB 消費者範本撰寫的應用程式。 測試取用者應該涵蓋您的提供者 （所有程式碼，您已加入或修改） 的所有功能區域。

1. 測試使用與 ADO 撰寫的取用者應用程式的提供者。 大部分的開發人員 （特別是 Microsoft Visual Basic 和 Microsoft C# 開發人員） 會使用 ADO 或 ADO.NET 取用者應用程式。 測試取用者應該涵蓋您的提供者的所有功能區域。 如需 ADO 取用者應用程式的範例，請參閱 < [Microsoft Visual Basic 中的 ADO 程式碼範例](https://msdn.microsoft.com/library/ms807514.aspx)。

1. 執行 OLE DB 一致性測試 （包括 ADO 一致性測試），以顯示您的提供者符合層級 0 的標準，OLE DB 提供者。 (如需層級 0 的說明，搜尋**OLE DB 層級 0 一致性測試**在[OLE DB 程式設計人員指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。 這些測試與相關聯的文件會包含具有視覺效果C++Data Access SDK 中。 這些測試也會協助顯示您的提供者執行其他彙總時，也[服務提供者](../../data/oledb/ole-db-resource-pooling-and-services.md)時特別有用，如果您修改或新增屬性。 如需有關一致性測試的詳細資訊，請參閱 Data Access SDK，位於其中一個 Visual Studio Cd 上讀我檔案。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)