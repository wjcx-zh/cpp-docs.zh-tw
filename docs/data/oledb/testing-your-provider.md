---
title: "測試您的提供者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 551ccfdf236eb5828b1d41ae8867acdb259b1d4f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="testing-your-provider"></a>測試提供者
發行的提供者之前，您應該執行下列測試，依照所示的順序。 這些測試確認正確大部分潛在的使用者提供者的功能。  
  
1.  測試使用的提供者[消費者](../../data/oledb/creating-an-ole-db-consumer.md)使用 OLE DB 消費者樣板撰寫的應用程式。 測試取用者應該涵蓋您的提供者 （所有程式碼加入或修改） 的所有功能區域。  
  
2.  測試使用與 ADO 撰寫的取用者應用程式的提供者。 大部分的開發人員 （特別是 Microsoft Visual Basic 和 C# Microsoft 開發人員） 會使用 ADO 或 ADO.NET 取用者應用程式。 測試取用者應該涵蓋您的提供者的所有功能區域。 如需 ADO 取用者應用程式的範例，請參閱[ADO 程式碼範例在 Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx)。  
  
3.  執行 OLE DB 一致性測試 （包括 ADO 一致性測試），以確保您的提供者符合 OLE DB 提供者層級 0 的標準。 (如需層級 0 的說明，搜尋 「 OLE DB 層級 0 一致性測試 」 在[OLE DB 程式設計人員指南](http://go.microsoft.com/fwlink/p/?linkid=121548)。 這些測試和相關聯的文件隨附於 Visual c + + Data Access SDK 中。 這些測試也有助於確保您的提供者執行其他彙總時正常[服務提供者](../../data/oledb/ole-db-resource-pooling-and-services.md)，如果您修改或加入屬性時特別有用。 如需有關一致性測試的詳細資訊，請參閱 Data Access SDK，其中一個 Visual Studio Cd 上的讀我檔案。  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)