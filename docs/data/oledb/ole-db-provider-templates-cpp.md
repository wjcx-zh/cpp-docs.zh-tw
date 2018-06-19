---
title: OLE DB 提供者樣板 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a331e72433ca25d280d35edfd33a56402675aea9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112741"
---
# <a name="ole-db-provider-templates-c"></a>OLE DB 提供者樣板 (C++)
OLE DB 是 Microsoft 通用資料存取策略中很重要的一部分。 OLE DB 設計可讓您從任何資料來源的高效能資料存取。 可透過 OLE DB 不論它是否來自資料庫檢視任何表格式資料。 這種彈性提供極大的電源。  
  
 中所述[OLE DB 消費者和提供者](../../data/oledb/ole-db-consumers-and-providers.md)，OLE DB 使用消費者和提供者的概念。 取用者會要求資料。提供者取用者以表格式格式傳回資料。 程式設計的觀點而言，這個模型的最重要的用意是提供者必須實作可讓取用者的任何呼叫。  
  
## <a name="what-is-a-provider"></a>什麼是提供者？  
 OLE DB 提供者是一組服務取用者物件的介面呼叫的 COM 物件，從持久的來源 （稱為資料存放區） 的表格式格式的資料傳送給取用者。  
  
 提供者可以很簡單或很複雜。 提供者可以支援最少量的功能或完全成熟的實際執行品質提供者藉由實作多個介面。 提供者可以傳回資料表，允許用戶端，以判斷該資料表的格式並對該資料執行作業。  
  
 每個提供者會實作一組標準的 COM 物件來處理要求用戶端，以標準任何 OLE DB 取用者可以從任何提供者，不論語言 （例如 c + + 和基本） 存取資料。  
  
 每個 COM 物件會包含數個介面，其中有些是必要，而其中有些是選擇性。 藉由實作必要的介面，提供者可確保任何用戶端應該能夠使用的功能 （稱為相容性） 的最低層級。 提供者可實作以提供其他功能的選擇性介面。 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)這些介面的詳細資料。 用戶端應該一律呼叫`QueryInterface`決定提供者是否支援指定的介面。  
  
## <a name="ole-db-specification-level-support"></a>OLE DB 規格的層級支援  
 OLE DB 提供者範本支援的 OLE DB 版本 2.7 規格。 使用 OLE DB 提供者範本，您可以實作層級 0 相容的提供者。 提供者範例中，例如，會使用範本來實作 non-MS-DOS 命令的伺服器執行 DOS DIR 命令來查詢檔案系統。 提供者範例會傳回目錄資訊的資料列集，這是標準 OLE DB 機制傳回表格式資料中。  
  
 最簡單的 OLE DB 範本所支援的提供者的類型是唯讀的提供者，使用任何命令。 也支援使用命令的提供者，以及建立書籤和讀取/寫入功能。 您可以撰寫額外的程式碼來實作讀取/寫入提供者。 動態資料列集和交易不支援最新版本，但如果您要新增它們。  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>您需要時建立的 OLE DB 提供者？  
 您不一定需要建立自己的提供者。Microsoft 提供數個預先封裝的標準提供者，在**資料連結屬性**Visual c + + 中的對話方塊。 若要建立 OLE DB 提供者的主要原因是利用通用資料存取策略。 這麼做的優點，包括：  
  
-   透過任何語言，例如 c + +、 Basic 和 Visual Basic Scripting Edition 中存取資料。 它可讓您組織中不同的程式設計人員存取相同的資料相同的方式，不論使用哪種語言。  
  
-   公開您的資料與其他資料來源 SQL Server、 Excel 和 Access 等。 這可以是非常有用，如果您想要不同的格式之間傳送資料。  
  
-   參與跨資料來源 （異質性） 作業。 這可以是非常有效的資料倉儲的方法。 藉由使用 OLE DB 提供者，您可以將資料保存在原生格式，並仍然能夠存取在簡單的作業。  
  
-   將額外的功能加入至您的資料，例如查詢處理。  
  
-   增加所控制的操作方式存取資料的效能。  
  
-   增加強固性。 如果您有專屬的資料格式，只有一個程式設計師可以存取，您有風險。 使用 OLE DB 提供者，可以開啟該專屬格式，您的程式設計人員。  
  
## <a name="read-only-and-updatable-providers"></a>唯讀和可更新的提供者  
 提供者有極大的複雜性和功能。 它可用於分類成唯讀提供者和可更新的提供者的提供者：  
  
-   Visual c + + 6.0 支援只有唯讀提供者。 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)討論如何建立唯讀提供者。  
  
-   Visual c + + 支援可更新的提供者，這可以更新 （寫入） 資料存放區。 可更新的提供者的相關資訊，請參閱[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例是可更新的提供者的範例。  
  
 如需詳細資訊，請參閱:  
  
-   [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>另請參閱  
 [資料存取](../data-access-in-cpp.md)   
 [OLE DB SDK 文件](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)