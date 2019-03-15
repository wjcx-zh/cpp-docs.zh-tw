---
title: 說明檔 (WinHelp)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
ms.openlocfilehash: 376d9faa87868cce842a1cb70273e220ff691fa4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825003"
---
# <a name="help-files-winhelp"></a>說明檔 (WinHelp)

當您在 MFC 應用程式精靈的[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)頁面中，藉由選取 [即時線上說明] 核取方塊，然後選取 [WinHelp 格式]，將 WinHelp 類型的說明支援新增至應用程式時，會建立下列檔案。

|檔案名稱|目錄位置|方案總管位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Projname*\hlp|原始程式檔|說明編譯器用來建立程式或控制項說明檔的說明專案檔。|
|*Projname*.rtf|*Projname*\hlp|說明檔|包含您可以編輯的範本主題以及有關自訂 .hpj 檔的資訊。|
|*Projname*.cnt|*Projname*\hlp|說明檔|提供 Windows 說明中 [內容] 視窗的結構。|
|Makehelp.bat|*Projname*|原始程式檔|由系統用來在編譯專案時，建置說明專案。|
|Print.rtf|*Projname*\hlp|說明檔|在您的專案包含列印支援 (預設值) 時建立。 描述列印命令和對話方塊。|
|*.bmp|*Projname*\hlp|資源檔|包含產生之不同說明檔主題的影像。|

您可以將 WinHelp 支援新增至 MFC ActiveX 控制項專案，方法是在 [MFC ActiveX 控制項精靈] 的[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)索引標籤中選取 [產生說明檔]。 當您將說明支援新增至 MFC ActiveX 控制項時，下列檔案會新增至您的專案：

|檔案名稱|目錄位置|方案總管位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Projname*\hlp|原始程式檔|說明編譯器用來建立程式或控制項說明檔的專案檔。|
|*Projname*.rtf|*Projname*\hlp|專案|包含您可以編輯的範本主題以及自訂 .hpj 檔的相關資訊。|
|Makehelp.bat|*Projname*|原始程式檔|由系統用來在編譯專案時，建置說明專案。|
|Bullet.bmp|*Projname*|資源檔|由標準說明檔主題用來代表項目符號清單。|

## <a name="see-also"></a>另請參閱

[為 Visual C++ 專案建立的檔案類型](file-types-created-for-visual-cpp-projects.md)
