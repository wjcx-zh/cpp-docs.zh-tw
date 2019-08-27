---
title: MFC 應用程式精靈、進階功能
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: dc2b745bf97dff65a3612c29745c9d0e455a347d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507812"
---
# <a name="advanced-features-mfc-application-wizard"></a>MFC 應用程式精靈、進階功能

本主題列出應用程式的其他功能選項，例如說明、列印支援等。 請在各章節中，指明這些進階功能的額外支援。

- **即時線上說明 (HTML)**

   產生即時線上說明的一組說明檔, 可使用 F1 和 [說明] 功能表, 或按一下對話方塊上的 [說明] 按鈕。 必須有說明編譯器才能支援 [說明]。 如果沒有說明編譯器，可重新執行安裝程式進行安裝。

   請[參閱 HTML 說明:程式](../../mfc/html-help-context-sensitive-help-for-your-programs.md)和說明檔[(HTML 說明)](../../build/reference/help-files-html-help.md)的即時線上說明, 以取得詳細資訊。

- **列印和預覽列印**

   藉由呼叫 MFC 程式庫的[CView 類別](../../mfc/reference/cview-class.md)中的成員函式, 產生程式碼來處理列印、列印設定和預覽列印命令。 精靈也會將這些函式的命令加入應用程式的功能表中。 列印支援僅適用于在 Wizard 的 [[應用程式類型]、[MFC 應用程式精靈]](../../mfc/reference/application-type-mfc-application-wizard.md)頁面中指定**檔/視圖架構支援**的應用程式。 在預設情況下，文件 / 檢視應用程式皆有列印支援。

- **Automation**

   指定應用程式可處理另一個應用程式中實作的物件，或將應用程式公開至 Automation 用戶端。

- **ActiveX 控制項**

   支援 ActiveX 控制項 (預設)。 如果您未選取此選項, 且稍後想要在專案中插入 ActiveX 控制項, 您必須在應用程式的[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)成員函式中新增對[AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer)的呼叫。

- **MAPI (訊息 API)**

   指定應用程式可建立、操作、傳輸和儲存郵件訊息。

- **Windows 通訊端**

   支援 Windows Sockets，您可以用來撰寫在 TCP/IP 網路上通訊的應用程式。

- **Active Accessibility**

   新增[IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible)至[CWnd](../../mfc/reference/cwnd-class.md)衍生類別的支援, 可讓您自訂使用者介面, 以便與協助工具用戶端進行更佳的互動。

- **通用控制項資訊清單**

   預設為啟用。 產生應用程式資訊清單，以啟用 Microsoft Windows XP 和新作業系統中的通用控制項 DLL。

   6\.0 版的通用控制項 DLL 不會自動更新目前應用程式所使用的舊版通用控制項。 若要使用 6.0 版的通用控制項 DLL，您必須建立應用程式資訊清單，以引導應用程式載入此 DLL。 這個通用控制項 DLL 也支援 Windows XP 主題。

   應用程式資訊清單也可以指定您的應用程式所需的其他 DLL 和版本。 如需應用程式資訊清單的詳細資訊, 請參閱 Windows SDK 中的[隔離應用程式和並存元件](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)。

- **支援重新開機管理員**

   新增[Windows 重新開機管理員](/windows/win32/RstMgr/using-restart-manager)的支援。 這部影片說明如何使用 MFC 的重新開機管理員:[How Do I:使用新的重新開機](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100))管理員。

- **先進的框架窗格**

   |選項|描述|
   |------------|-----------------|
   |**Explorer 停駐窗格**|建立一個停駐窗格, 類似于主框架視窗左邊的 Visual Studio**方案總管**。|
   |**輸出停駐框架**|建立一個停駐窗格, 類似于主框架視窗底下的 [Visual Studio**輸出**] 窗格。|
   |**屬性停駐窗格**|建立一個停駐窗格, 類似于主框架視窗右邊的 [Visual Studio**屬性**] 窗格。|
   |**流覽窗格**|在主框架視窗左邊，建立類似 Outlook 巡覽列的停駐窗格。|
   |**標題列**|在主框架視窗上方建立 Office 樣式的標題列。|

- **最近使用的檔案清單上的檔案數目**

   指定最近使用的檔案清單中列出的檔案數量。 預設值為 4。

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)
