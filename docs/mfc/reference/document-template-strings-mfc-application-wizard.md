---
title: "文件樣板字串，MFC 應用程式精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d2fdabb971ab9aad06f5500b98e9d8591266c85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-strings-mfc-application-wizard"></a>MFC 應用程式精靈、文件樣板字串
在 MFC 應用程式精靈的這個頁面上，提供或修改下列選項，以協助文件管理和當地語系化。 文件樣板字串可包含應用程式，供**文件/檢視架構支援**中[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)。 不提供對話方塊。 因為大部分的文件樣板字串是否可見並使用應用程式的使用者，他們會當地語系化成**資源語言**中指出**應用程式類型**精靈頁面。  
  
 **未當地語系化的字串**  
 適用於建立使用者文件的應用程式。 使用者可以開啟、 列印及儲存的文件更輕鬆地如果您提供的副檔名和檔案類型識別碼。 因為它們由系統中，而不是由使用者使用，這些項目不會進行當地語系化。  
  
|選項|描述|  
|------------|-----------------|  
|**副檔名**|設定使用者儲存時使用的應用程式的文件相關聯的副檔名。 例如，如果您的專案為小工具，您可以將命名檔案副檔名.wgt。 （當您輸入檔案的副檔名時，不包含句號。）<br /><br /> 如果您提供的檔案副檔名，[總管] 可以列印您的應用程式文件，而不啟動應用程式，使用者將文件圖示的印表機圖示上的時候。<br /><br /> 如果您未指定擴充功能，使用者必須在儲存檔案時指定副檔名的檔案。 精靈不會提供預設的副檔名。|  
|**檔案類型識別碼**|在系統登錄中設定文件類型的標籤。|  
  
 **當地語系化的字串**  
 產生相關聯的應用程式和文件會讀取和使用應用程式的使用者，因此字串已當地語系化的字串。  
  
|選項|描述|  
|------------|-----------------|  
|**Language**|表示的語言下的所有方塊都顯示字串**當地語系化字串**。 若要變更的值，此方塊中，選取適當的語言下**資源語言**中[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 應用程式精靈頁面。|  
|**主框架標題**|設定出現在主應用程式框架最上方的文字。 根據預設，專案名稱。|  
|**文件類型名稱**|識別您可以在其下群組應用程式的文件的文件的類型。 根據預設，專案名稱。 變更預設不會變更在此對話方塊中的任何其他選項。|  
|**篩選器名稱**|設定您的使用者可以指定要尋找的檔案類型的檔案名稱。 此選項可從**檔案類型**和**存檔類型**標準的 Windows 中的選項**開啟**和**存**對話方塊。 根據預設，專案名稱和檔案的內容，後面接著在提供的擴充功能**副檔名**。 例如，如果您的專案名稱為 Widget，且副檔名為.wgt，**篩選器名稱**預設為 Widget 檔案 (*.wgt)。|  
|**檔案的新簡短名稱**|設定標準的視窗中顯示的名稱`New`對話方塊中，如果有多個新的文件範本。 如果您的應用程式是[Automation 伺服程式](../../mfc/automation-servers.md)，這個名稱會當做 Automation 物件的簡短名稱。 根據預設，專案名稱。|  
|**檔案類型完整名稱**|設定系統登錄中的檔案類型名稱。 Automation 伺服應用程式時，此名稱會為您的 Automation 物件的完整名稱。 根據預設，專案名稱加上。文件。|  
  
## <a name="see-also"></a>請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)

