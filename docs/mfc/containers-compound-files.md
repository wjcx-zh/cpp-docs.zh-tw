---
title: "容器： 複合檔案 |Microsoft 文件"
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
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 261fcca76b4a5c9a6cb329081028672b2f241576
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="containers-compound-files"></a>容器：複合檔案
本文說明複合檔案的元件和實作，以及於 OLE 應用程式使用複合檔案的優點和缺點。  
  
 複合檔案是 OLE 的整數部分。 它們是用來加速資料傳輸和 OLE 文件儲存。 複合檔案是主動式結構化儲存體模型的實作。 一致的介面支援序列化為儲存區、資料流或檔案物件。 `COleStreamFile` 類別和 `COleDocument` 在 MFC 程式庫中支援複合檔案。  
  
> [!NOTE]
>  使用複合檔案不表示資訊來自 OLE 文件或複合文件。 複合檔案只是儲存複合文件、OLE 文件和其他資料的其中一個方式。  
  
##  <a name="_core_components_of_a_compound_file"></a>複合檔案的元件  
 複合檔案的 OLE 實作使用三個物件類型：資料流物件、儲存物件和 `ILockBytes` 物件。 這些物件類似於標準檔案系統的元件，如下所示：  
  
-   如檔案等資料流物件，會儲存任何類型的資料。  
  
-   如目錄等儲存物件，可包含其他儲存區和資料流物件。  
  
-   **LockBytes**物件代表儲存物件和實體硬體之間的介面。 它們決定實際位元組寫入至任何存放裝置的方式**LockBytes**正在存取的物件，例如硬碟或全域記憶體區域。 如需有關**LockBytes**物件和`ILockBytes`介面，請參閱*OLE 程式設計人員參考*。  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a>複合檔案的優缺點  
 複合檔案提供了早期儲存檔案方法所沒有的優點。 包括：  
  
-   累加檔案存取。  
  
-   檔案存取模式。  
  
-   檔案結構標準化。  
  
 在決定是否在應用程式中使用複合檔案時，應考慮複合檔案 (與軟碟儲存體相關的大型和效能問題) 的可能缺點。  
  
###  <a name="_core_incremental_access_to_files"></a>累加存取檔案  
 累加存取檔案是使用複合檔案中自動效益。 由於複合檔案可視為「檔案內的檔案系統」，個別物件類型 (例如資料流或儲存區) 可以直接存取而不需要載入整個檔案。 這可大幅減少應用程式需要用於由使用者存取需編輯之新物件的時間。 根據相同概念，累加更新提供相似的效益。 OLE 不會用儲存整個檔案的方式儲存對一個物件所做的變更，它只會儲存資料流或使用者所編輯的儲存物件。  
  
###  <a name="_core_file_access_modes"></a>檔案存取模式  
 判斷複合檔案中對物件所做的變更何時被認可至磁碟的能力，是使用複合檔案的另一個效益。 檔案存取模式 (不是交易模式就是直接存取模式) 決定何時認可變更。  
  
-   交易模式使用兩階段交易認可作業，在複合檔案中對物件進行變更，因此可以同時保留文件的舊複本和新複本，直到使用者選擇要儲存或復原變更為止。  
  
-   直接存取模式會直接將產生的變更合併到文件中，無需在稍後將變更復原。  
  
 如需有關存取模式的詳細資訊，請參閱*OLE 程式設計人員參考*。  
  
###  <a name="_core_standardization"></a>標準化  
 複合檔案標準化結構可讓不同的 OLE 應用程式瀏覽您的 OLE 應用程式所建立的複合檔案，不需了解實際建立檔案的應用程式。  
  
###  <a name="_core_size_and_performance_considerations"></a>大小和效能考量  
 由於複合檔案儲存結構和能力的複雜度，以及累加儲存資料的能力，使用這種格式的檔案通常比使用非結構化或「一般檔案」儲存區的其他檔案來的大一些。 如果您的應用程式經常載入和儲存檔案，使用複合檔案比非複合檔案更可能造成檔案大小快速增加。 由於複合檔案會變大，存放在磁片及從磁片載入的檔案存取時間可能也會受到影響，導致對檔案的存取速度變慢。  
  
 影響效能的另一個問題是複合檔案分散。 複合檔案的大小取決於檔案使用的第一個和最後一個磁碟磁區之間的差異。 分散的檔案可能包含許多不包含資料的可用空間區域，不過在計算大小時會被計算進去。 在複合檔案的存留期內，這些區域由儲存物件的插入或刪除建立。  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a>為您的資料使用複合檔案格式。  
 在成功建立具有衍生自 `COleDocument` 之文件類別的應用程式後，請確定您的主要文件建構函式呼叫 `EnableCompoundFile`。 當應用程式精靈建立 OLE 容器應用程式時，會為您插入這個呼叫。  
  
 在*OLE 程式設計人員參考*，請參閱[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)， [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)，和[ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238)。  
  
## <a name="see-also"></a>請參閱  
 [容器](../mfc/containers.md)   
 [容器： 使用者介面問題](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile 類別](../mfc/reference/colestreamfile-class.md)   
 [COleDocument 類別](../mfc/reference/coledocument-class.md)
