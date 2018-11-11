---
title: 說明檔 (HTML 說明)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: dc98e9794200e2a317c7db2b0b513a254efff275
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480375"
---
# <a name="help-files-html-help"></a>說明檔 (HTML 說明)

當您在 MFC 應用程式精靈的[進階功能](../mfc/reference/advanced-features-mfc-application-wizard.md)頁面中，藉由選取 [即時線上說明] 核取方塊，然後選取 [HTML 說明格式]，將 HTML 說明類型的說明支援新增至應用程式時，會建立下列檔案。

|檔案名稱|目錄位置|方案總管位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hhp|*Projname*\hlp|HTML 說明檔|說明專案檔。 它包含將說明檔編譯為 .hxs 檔或 .chm 檔所需的資料。|
|*Projname*.hhk|*Projname*\hlp|HTML 說明檔|包含說明主題的索引。|
|*Projname*.hhc|*Projname*\hlp|HTML 說明檔|説明專案的內容。|
|Makehtmlhelp.bat|*Projname*|原始程式檔|由系統用來在編譯專案時，建置說明專案。|
|Afxcore.htm|*Projname*\hlp|HTML 說明主題|包含標準 MFC 命令和螢幕物件的標準說明主題。 將您自己的說明主題新增至此檔案。|
|Afxprint.htm|*Projname*\hlp|HTML 說明主題|包含列印命令的說明主題。|
|*.jpg; \*.gif|*Projname*\hlp\Images|資源檔|包含產生之不同說明檔主題的影像。|

## <a name="see-also"></a>請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)