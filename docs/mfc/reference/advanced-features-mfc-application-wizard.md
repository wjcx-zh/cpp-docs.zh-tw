---
title: 進階功能，MFC 應用程式精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5094c18f72182929565e7c23c38b63443839da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358452"
---
# <a name="advanced-features-mfc-application-wizard"></a>MFC 應用程式精靈、進階功能
本主題列出應用程式的其他功能選項，例如說明、列印支援等。 請在各章節中，指明這些進階功能的額外支援。  
  
 **即時線上說明 (HTML)**  
 會產生一組即時線上說明，請使用 F1 使用 說明 功能表中，或按一下說明檔案**協助** 對話方塊上的按鈕。 必須有說明編譯器才能支援 [說明]。 如果沒有說明編譯器，可重新執行安裝程式進行安裝。  
  
 請參閱[HTML 說明： 程式的即時線上說明](../../mfc/html-help-context-sensitive-help-for-your-programs.md)和[說明檔 （HTML 說明）](../../ide/help-files-html-help.md)如需詳細資訊。  
  
 **列印和預覽列印**  
 產生程式碼來處理列印、 列印設定和預覽列印命令藉由呼叫成員函式中[CView 類別](../../mfc/reference/cview-class.md)從 MFC 程式庫。 精靈也會將這些函式的命令加入應用程式的功能表中。 列印支援會指定的應用程式僅供**文件/檢視架構支援**中[應用程式類型、 MFC 應用程式精靈](../../mfc/reference/application-type-mfc-application-wizard.md)精靈頁面。 在預設情況下，文件 / 檢視應用程式皆有列印支援。  
  
 **Automation**  
 指定應用程式可處理另一個應用程式中實作的物件，或將應用程式公開至 Automation 用戶端。  
  
 **ActiveX 控制項**  
 支援 ActiveX 控制項 (預設)。 如果您不選取此選項與稍後想要插入您的專案中的 ActiveX 控制項，您必須將呼叫加入[AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer)應用程式中[Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)成員函式。  
  
 **MAPI (訊息 API)**  
 指定應用程式可建立、操作、傳輸和儲存郵件訊息。  
  
 **Windows 通訊端**  
 支援 Windows Sockets，您可以用來撰寫在 TCP/IP 網路上通訊的應用程式。  
  
 **Active Accessibility**  
 新增支援[Cwnd](http://msdn.microsoft.com/library/windows/desktop/dd318466)至[CWnd](../../mfc/reference/cwnd-class.md)-衍生的類別，您可以使用自訂使用者介面的更佳的協助工具用戶端互動。  
  
 **通用控制項資訊清單**  
 預設為啟用。 產生應用程式資訊清單，以啟用 Microsoft Windows XP 和新作業系統中的通用控制項 DLL。  
  
 6.0 版的通用控制項 DLL 不會自動更新目前應用程式所使用的舊版通用控制項。 若要使用 6.0 版的通用控制項 DLL，您必須建立應用程式資訊清單，以引導應用程式載入此 DLL。 這個通用控制項 DLL 也支援 Windows XP 主題。  
  
 應用程式資訊清單也可以指定您的應用程式所需的其他 DLL 和版本。 如需應用程式資訊清單的詳細資訊，請參閱[隔離的應用程式和-並存組件](http://msdn.microsoft.com/library/dd408052)Windows SDK 中。  
  
 **支援重新啟動管理員**  
 新增支援[Windows 重新啟動管理員](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx)。 這部影片示範如何使用 MFC 的重新啟動管理員：[如何： 使用新的重新啟動管理員](http://msdn.microsoft.com/vstudio/ee886407)。  
  
 **進階的框架窗格**  
 |選項|描述|  
|------------|-----------------|  
|**總管停駐窗格**|建立類似 Visual Studio 的停駐窗格**方案總管 中**主框架視窗的左邊。|  
|**輸出停駐**|建立類似 Visual Studio 的停駐窗格**輸出**位於主框架視窗下的窗格。|  
|**屬性停駐窗格**|建立類似 Visual Studio 的停駐窗格**屬性**主框架視窗右邊的窗格。|  
|**瀏覽窗格**|在主框架視窗左邊，建立類似 Outlook 巡覽列的停駐窗格。|  
|**標題列**|在主框架視窗上方建立 Office 樣式的標題列。|  
  
 **最近使用的檔案清單上的檔案數目**  
 指定最近使用的檔案清單中列出的檔案數量。 預設值為 4。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)

