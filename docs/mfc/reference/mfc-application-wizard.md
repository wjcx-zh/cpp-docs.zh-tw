---
title: MFC 應用程式精靈
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351826"
---
# <a name="mfc-application-wizard"></a>MFC 應用程式精靈

MFC 應用程式精靈產生一個應用程式,在編譯時實現 Windows 可執行 (.exe) 應用程式的基本功能。 MFC 初學者應用程式包括C++源 (.cpp) 檔案、資源 (.rc) 檔案、標頭 (.h) 檔和專案 (.vcxproj) 檔。 在這些初學者檔中生成的代碼基於 MFC。

> [!NOTE]
> 根據您選擇的選項,嚮導會在項目中創建其他檔。 例如,如果在[「高級功能」](../../mfc/reference/advanced-features-mfc-application-wizard.md)頁上選擇**上下文相關説明**,嚮導將創建編譯專案説明檔所需的檔。 有關嚮導創建的檔的詳細資訊,請參閱[為 Visual Studio C++專案創建的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md),並在專案中查看 Readme.txt 檔。

## <a name="overview"></a>概觀

此嚮導頁描述要創建的 MFC 應用程式的當前應用程式設置。 預設情況下,精靈建立專案如下:

- [MFC 應用程式精靈、應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)

  - 專案使用選項卡式多文檔介面 (MDI) 支援創建。 有關詳細資訊,請參閱[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。

  - 該專案使用[文件/檢視體系結構](../../mfc/document-view-architecture.md)。

  - 該專案使用 Unicode 庫。

  - 該專案使用 Visual Studio 專案樣式創建,並支援視覺樣式切換。

  - 專案在共用 DLL 中使用 MFC。 有關詳細資訊,請參閱[在可視化工作室中創建 C/C++ DLL。](../../build/dlls-in-visual-cpp.md)

- [MFC 應用程式精靈、複合文件支援](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - 該專案不提供復合文件的支援。

- [MFC 應用程式精靈、文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - 專案使用專案名稱作為預設文件範本字串。

- [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)

  - 該專案不提供資料庫支援。

- [MFC 應用程式精靈、使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - 該專案實現標準 Windows 使用者介面功能,如系統功能表、狀態列、最大化和最小化框 **、「關於」** 框、標準選單欄和停靠工具列以及子框架。

- [MFC 應用程式精靈、進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - 該專案支援列印和列印預覽。

  - 該專案支援 ActiveX 控件。 有關詳細資訊,請參閱建立[ActiveX 控制項的操作序列](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。

  - 該專案不支援[自動化](../../mfc/automation.md)[、MAPI、Windows](../../mfc/mapi-support-in-mfc.md)[套接字](../../mfc/windows-sockets-in-mfc.md)或活動輔助功能。

  - 該專案支援**資源管理員**停靠窗格、**輸出**停靠窗格和**屬性**停靠窗格。

- [MFC 應用程式精靈、產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - 項目的檢視類別派生自[CView 類別](../../mfc/reference/cview-class.md)。

  - 該專案的應用程式類別派生自[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。

  - 項目的文件類別的[CDocument 類別](../../mfc/reference/cdocument-class.md)。

  - 該專案的主框架類別的主式自[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。

  - 該專案的子框架類別的子式自[CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)。

要更改這些預設設置,請按一下嚮導左列中的相應選項卡標題,然後對顯示的頁面上進行更改。

創建 MFC 應用程式專案後,可以使用 VisualC++[代碼嚮導](../../ide/adding-functionality-with-code-wizards-cpp.md)向專案添加物件或控制項。

## <a name="see-also"></a>另請參閱

[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC 傳統型應用程式](../../mfc/mfc-desktop-applications.md)<br/>
[使用類別來編寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)
