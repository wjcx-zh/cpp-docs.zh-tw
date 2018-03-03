---
title: "文件樣板字串 MFC 加入類別精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9d37b1a886c28d267cd7a387317edce6bf7f3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>MFC 加入類別精靈、文件範本字串
精靈的這個頁面只是為了符合下列準則的類別有：  
  
-   MFC 專案支援的文件/檢視架構。  
  
-   新類別的基底類別是[CFormView](../../mfc/reference/cformview-class.md)。  
  
-   核取方塊**產生 DocTemplate 資源**上核取**名稱**區段[MFC 類別精靈](../../mfc/reference/mfc-add-class-wizard.md)。  
  
 精靈會提供下列的值，以協助使用表單檢視的設計、 管理和當地語系化的預設值。 因為大部分的文件樣板字串是否可見並使用表單的使用者，他們會當地語系化成**資源語言**中指出[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 應用程式精靈頁面建立專案時。  
  
> [!NOTE]
>  精靈不支援自動列印類別衍生自`CFormView`。  
  
 請參閱[文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)如需詳細資訊。  
  
## <a name="nonlocalized-strings"></a>未當地語系化的字串  
 適用於建立使用者文件的應用程式。 使用者可以開啟和儲存的文件更輕鬆地如果文件類型的副檔名和檔案類型識別碼。 因為它們由系統中，而不是由使用者使用，這些項目不會進行當地語系化。  
  
 **副檔名**  
 設定這個表單應用程式的文件類型相關聯的副檔名。 類別名稱為基礎的檔案副檔名預設值。 例如，如果新的 MFC 類別的名稱為**CWidget**，根據預設，檔案的副檔名是。 wid 檔案的副檔名用於檔案篩選器和**開啟**和**存**對話方塊。  
  
 如果您變更副檔名時，變更會反映在**篩選器名稱**方塊。  
  
> [!NOTE]
>  如果您變更預設的副檔名，不會包含句號。  
  
 **檔案類型識別碼**  
 在系統登錄中設定文件類型的標籤。  
  
## <a name="localized-strings"></a>當地語系化的字串  
 產生的表單與讀取和使用的應用程式的使用者，讓字串已當地語系化的文件相關聯的字串。  
  
 **文件類型名稱**  
 識別您可以在其下群組應用程式的文件的文件的類型。 根據預設，它為基礎的類別名稱。 例如，如果新的 MFC 類別的名稱為**CWidget**，根據預設，文件類型名稱是 Widget。 變更預設不會變更在此對話方塊中的任何其他選項。  
  
 **篩選器名稱**  
 設定使用者可以指定要尋找指定的檔案類型的檔案的名稱。 此選項可從**檔案類型**和**存檔類型**標準的 Windows 中的選項**開啟**和**存**對話方塊。 根據預設，名稱根據專案名稱加上檔案，然後再由延伸所示**副檔名**。 例如，如果您的專案名稱為 Widget，且副檔名為.wid，**篩選器名稱**預設為 Widget 檔案 (*.wid)。  
  
 **檔案的新簡短名稱**  
 設定標準的視窗中顯示的名稱`New`對話方塊中，如果專案具有一個以上的文件範本。 如果您的應用程式是[Automation 伺服程式](../../mfc/automation-servers.md)，這個名稱會當做 Automation 物件的簡短名稱。 根據預設，這個名稱根據類別名稱。  
  
 **檔案類型完整名稱**  
 設定系統登錄中的檔案類型名稱。 Automation 伺服應用程式時，此名稱會為您的 Automation 物件的完整名稱。 根據預設，這個名稱根據類別名稱加上。文件。 例如，如果類別名稱是**CWidget**、**檔案類型完整名稱**是 Widget 文件。  
  
 **文件類別**  
 表示專案的文件類別。 根據預設，這個類別是主應用程式的文件類別，如下所示[檢視產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)MFC 應用程式精靈頁面。 如果您在專案中加入了其他文件類別，您可以從清單中，選取另一個文件類別。  
  
## <a name="see-also"></a>請參閱  
 [MFC 加入類別精靈](../../mfc/reference/mfc-add-class-wizard.md)   
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)
