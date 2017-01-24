---
title: "MFC 加入類別精靈、文件範本字串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.doctemp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 加入類別精靈, 文件控制字串"
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 加入類別精靈、文件範本字串
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有符合下列準則的類別才能使用精靈的這個頁面：  
  
-   MFC 專案支援文件\/檢視架構。  
  
-   新類別的基底類別 \(Base Class\) 是 [CFormView](../../mfc/reference/cformview-class.md)。  
  
-   在 \[產生 DocTemplate 資源\] 核取方塊中，核取 [MFC 類別精靈](../../mfc/reference/mfc-add-class-wizard.md) 的 \[**名稱**\] 區段。  
  
 精靈會為下列值提供預設值來幫助表單檢視設計、管理及當地語系化。  由於多數文件樣板字串 \(Document Template String\) 都是可見的並且是由表單的使用者來使用，因此當建立專案時，它們會當地語系化為 MFC 應用程式精靈的[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面中所指示的**資源語言**。  
  
> [!NOTE]
>  精靈不會為衍生自 `CFormView` 的類別提供自動列印支援。  
  
 如需詳細資訊，請參閱[文件樣板和文件\/檢視建立處理序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 未當地語系化字串  
 套用至建立使用者文件的應用程式。  如果文件類型具有副檔名和檔案類型 ID，則使用者可較容易開啟和儲存文件。  這些項目之所以沒有當地語系化，是因為它們是由系統使用，而不是由使用者所使用。  
  
 **副檔名**  
 為這個表單應用程式設定與文件類型相關的副檔名。  副檔名預設值是根據類別名稱而定。  例如，如果新的 MFC 類別命名為 **CWidget**，則副檔名依照預設是 .wid。  副檔名會用在檔案篩選器和 \[開啟\] 及 \[另存新檔\] 對話方塊。  
  
 如果您變更副檔名，則變更會反映在 \[篩選條件名稱\] 方塊中。  
  
> [!NOTE]
>  如果您變更預設副檔名，請不要包含句號。  
  
 **檔案類型 ID**  
 設定系統註冊區中的文件類型的標籤。  
  
## 已當地語系化字串  
 產生與表單和文件相關聯字串，讓應用程式的使用者能夠讀取和使用，所以將字串當地語系化。  
  
 **文件類型名稱**  
 識別出應用程式的文件可歸類的文件類型。  依照預設，它是根據類別的名稱而定。  例如，如果新的 MFC 類別命名為 **CWidget**，則文件類型名稱依照預設是 Widget。  變更預設並不會改變本對話方塊中的任何其他選項。  
  
 **篩選條件名稱**  
 設定名稱讓使用者可指示以尋找特定檔案類型的檔案。  本選項位於標準 Windows \[開啟舊檔\] 和 \[另存新檔\] 對話方塊中的 \[檔案類型\] 和 \[**存檔類型**\] 選項中。  依照預設，名稱是根據專案名稱加上 Files，後面再跟著 \[副檔名\] 中指示的副檔名。  例如，如果您的專案名稱是 Widget，而副檔名是 .wid，則 \[篩選條件名稱\] 依照預設是 Widget Files \(\*.wid\)。  
  
 **檔案新簡短名稱**  
 設定出現在標準 Windows \[`New`\] 對話方塊的名稱 \(如果專案具有一個以上的文件樣板\)。  如果您的應用程式為 [Automation 伺服程式](../../mfc/automation-servers.md)，本名稱可做為 Automation 物件的簡短名稱。  依照預設，這個名稱是根據類別名稱來命名。  
  
 **檔案類型完整名稱**  
 設定系統註冊區中的檔案類型名稱。  如果您的應用程式為 Automation 伺服程式，則本名稱可用來做為 Automation 物件的完整名稱。  依照預設，這個名稱是根據類別名稱再加上 .Document。  例如，如果類別名稱是 **CWidget**，\[檔案類型完整名稱\] 就是 Widget Document。  
  
 **文件類別**  
 指示專案的文件類別。  依照預設，這個類別是主應用程式的文件類別，如 MFC 應用程式精靈中的[檢視產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面中所列。  如果您已將其他文件類別加入至專案中，您可從清單中選取其他文件類別。  
  
## 請參閱  
 [MFC 加入類別精靈](../../mfc/reference/mfc-add-class-wizard.md)   
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)