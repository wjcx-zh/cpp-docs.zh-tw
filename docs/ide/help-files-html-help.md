---
title: "說明檔 （HTML 說明） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c96cd6ad904439f556f2baa51602353ea00c5ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="help-files-html-help"></a>說明檔 (HTML 說明)
當選取 加入應用程式的說明支援的 HTML 說明類型會建立下列檔案**即時線上說明**核取方塊，然後選取  **HTML 說明格式**中[進階功能](../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 應用程式精靈頁面。  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hhp|*Projname*\hlp|HTML 說明檔|說明專案檔中。 它包含編譯為.hxs 檔的說明檔或.chm 檔案所需的資料。|  
|*Projname*.hhk|*Projname*\hlp|HTML 說明檔|包含索引的說明主題。|  
|*Projname*.hhc|*Projname*\hlp|HTML 說明檔|說明專案的內容。|  
|Makehtmlhelp.bat|*專案名稱*|原始程式檔|用來編譯專案時，建置說明專案系統。|  
|Afxcore.htm|*Projname*\hlp|HTML [說明] 主題|包含標準 MFC 命令和螢幕物件的標準說明主題。 加入這個檔案中的說明主題。|  
|Afxprint.htm|*Projname*\hlp|HTML [說明] 主題|包含列印命令的說明主題。|  
|*.jpg;\*.gif|*Projname*\hlp\Images|資源檔|包含不同產生的說明檔主題的影像。|  
  
## <a name="see-also"></a>請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)