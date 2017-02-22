---
title: "容器：複合檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案的存取模式 [C++]"
  - "複合文件"
  - "複合檔案"
  - "容器 [C++], 複合檔案"
  - "文件 [C++], 複合"
  - "文件 [C++], OLE"
  - "檔案 [C++], 複合"
  - "OLE 容器, 複合檔案"
  - "OLE 文件, 複合檔案"
  - "效能 [C++], 複合檔案"
  - "標準化檔案結構複合檔案"
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 容器：複合檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明複合檔案的元件和實作和使用複合檔案的優點和缺點於 OLE 應用程式。  
  
 複合檔案是 OLE 的整數部分。  它們是用來加速資料傳輸和 OLE 文件儲存。  複合檔案是現用的結構化儲存體模型的實作。  一致的介面有支援序列化至儲存區、資料流或檔案物件。  複合檔案在 MFC 程式庫類別支援 `COleStreamFile` 和 `COleDocument`。  
  
> [!NOTE]
>  使用複合檔案不表示資訊來自 OLE 文件或複合文件。  複合檔案是一個方式儲存複合文件， OLE 文件和其他資料。  
  
##  <a name="_core_components_of_a_compound_file"></a> 複合檔案的元件  
 複合檔案的 OLE 實作使用三個物件型別:資料流物件、儲存物件和 `ILockBytes` 物件。  這些物件會以下列方式類似於標準檔案系統的元件:  
  
-   資料流物件，例如檔案，任何型別的資料。  
  
-   儲存物件，因為目錄，可能包含其他儲存區、資料流物件。  
  
-   **LockBytes** 物件代表儲存物件和實體硬體之間的介面。  它們決定實際位元組方式寫入任何儲存裝置 **LockBytes** 物件存取，例如硬碟或全域記憶體區域。  如需 **LockBytes** 物件和 `ILockBytes` 介面的詳細資訊，請參閱 *OLE 程式設計人員參考》*。  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> 複合檔案的優缺點。  
 複合檔案提供優點 null 以文件儲存較早的方法。  包括：  
  
-   將檔案存取。  
  
-   檔案存取模式。  
  
-   檔案結構的標準化  
  
 在您的應用程式時應該考慮複合檔案 \(大和效能問題的可能的缺點與軟體磁碟儲存體相關\)，在決定使用它們。  
  
###  <a name="_core_incremental_access_to_files"></a> 對檔案的存取加入  
 對檔案的增加存取是使用複合檔案中自動優點。  由於複合檔案可視為在檔案內的檔案系統，」各自的物件型別，例如資料流或儲存體，可以存取，而不需要載入整個檔案。  這可以大幅降低應用程式需要由使用者存取編輯的新物件的時間。  加入更新，根據相同概念，提供相似的優點。  而不是將整個檔案儲存所做的變更套用至物件， OLE 儲存使用者或儲存物件編輯的資料流。  
  
###  <a name="_core_file_access_modes"></a> 檔案存取模式。  
 可判斷物件的變更在複合檔案上時認可磁碟已使用複合檔案的另一項優點。  檔案存取，或交易或直接的方式，判斷變更時執行。  
  
-   交易模式使用兩階段交易認可作業對物件所做的變更會在複合檔案，同時保留文件可用的舊和新複本，直到使用者選擇要儲存或復原變更。  
  
-   即時模式合併對文件進行的變更，會使，，不用能力之後移除它們。  
  
 如需存取模式的詳細資訊，請參閱 *OLE 程式設計人員參考》*。  
  
###  <a name="_core_standardization"></a> 標準。  
 複合檔案標準化結構可讓不同的 OLE 應用程式將 OLE 應用程式建立的複合檔案瀏覽沒有實際的檔案建立應用程式的知識。  
  
###  <a name="_core_size_and_performance_considerations"></a> 尺寸與效能考量  
 由於複合檔案儲存結構和能力的複雜累加儲存資料檔案，會使用這個格式大於其他檔案常使用非結構化或「平坦檔」儲存區。  如果您的應用程式經常載入和儲存檔案，使用複合檔案比 noncompound 檔案可能會造成檔案大小快速加入。  由於複合檔案可以取得大，檔案的存取時間儲存了並從磁片載入可能也會受到影響，導致對檔案的速度較慢的存取。  
  
 影響效能的其他問題是複合檔案分割。  複合檔案的大小取決於檔案和最後扇磁碟區之間的差異使用的第一個。  已分割的檔案可能包含不包含資料可用空間的許多區域，不過，計數，在計算大小時。  在複合檔案的存留期內，這些區域由儲存物件的插入或刪除建立。  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> 使用複合檔案為您的資料格式。  
 在成功建立具有文件類別後的應用程式衍生自 `COleDocument`，請確定您的主要文件建構函式呼叫 `EnableCompoundFile`。  當應用程式精靈建立 OLE 容器應用程式時，插入這個呼叫您的。  
  
 在 *OLE 程序參考*，請參閱 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)、 [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)和 [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238)。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [容器：使用者介面問題](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile Class](../mfc/reference/colestreamfile-class.md)   
 [COleDocument Class](../mfc/reference/coledocument-class.md)