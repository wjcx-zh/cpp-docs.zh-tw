---
title: MFC 程式或控制項原始程式檔和標頭檔 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cb9518f60db98bd590cecdffa09ee7d814241ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447904"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC 程式或控制項原始程式檔和標頭檔

當您在 Visual Studio 中建立 MFC 專案時，會根據您為所建立專案選取的選項而建立下列檔案。 例如，只有當您建立對話方塊架構的專案或類別時，您的專案才會包含 *Projname*dlg.cpp 和 *Projname*dlg.h 檔案。

這些檔案全都位於 *Projname* 目錄下，以及 [方案總管] 的標頭檔 (.h 檔案) 資料夾或原始程式檔 (.cpp 檔) 資料夾中。

|檔案名稱|描述|
|---------------|-----------------|
|*Projname*.h|程式或 DLL 的主要包含檔。 它包含所有全域符號和其他標頭檔的 `#include` 指示詞。 它會從 `CWinApp` 衍生 `CPrjnameApp` 類別，並宣告 `InitInstance` 成員函式。 若為控制項，`CPrjnameApp` 類別是衍生自 `COleControlModule`。|
|*Projname*.cpp|主要原始程式檔。 它會針對衍生自 `CWinApp` 的 `CPrjnameApp` 類別建立一個物件，並覆寫 `InitInstance` 成員函式。<br /><br /> 若為可執行檔，`CPrjnameApp::InitInstance` 會執行數個作業。 它會註冊文件範本以作為文件與檢視之間的連線、建立主框架視窗，以及建立空白文件 (如果文件指定為應用程式的命令列引數，則會開啟文件)。<br /><br /> 若為 DLL 和 ActiveX (先前稱為 OLE) 控制項，`CProjNameApp::InitInstance` 會藉由呼叫 `COleObjectFactory::RegisterAll` 向 OLE 註冊控制項的物件 Factory，並呼叫 `AfxOLEInit`。 此外，成員函式 `CProjNameApp::ExitInstance` 可用來透過 **AfxOleTerm** 呼叫從記憶體卸載控制項。<br /><br /> 這個檔案也會藉由實作 `DllRegisterServer` 和 `DllUnregisterServer` 函式，在 Windows 系統註冊資料庫中註冊和取消註冊控制項。|
|*Projname*ctrl.h、*Projname*ctrl.cpp|宣告和實作 `CProjnameCtrl` 類別。 `CProjnameCtrl` 衍生自 `COleControl`，而且定義一些成員函式的基本結構實作，以初始化、繪製和序列化 (載入和儲存) 控制項。 也會定義訊息、事件和分派對應。|
|*Projname*dlg.cpp、*Projname*dlg.h|當您選擇對話方塊架構應用程式時建立。 這些檔案會衍生和實作名為 `CProjnameDlg` 的對話方塊類別，並包含基本結構成員函式來初始化對話方塊及執行對話方塊資料交換 (DDX)。 [關於] 對話方塊類別也放置在這些檔案中，而不是在 *Projname*.cpp 中。|
|Dlgproxy.cpp、Dlgproxy.h|在對話方塊架構程式中，為主要對話方塊之專案的自動化 Proxy 類別的實作和標頭檔。 只有在您已選擇自動化支援時，才會使用此項目。|
|*Projname*doc.cpp、*Projname*doc.h|衍生和實作名為 `CProjnameDoc` 的文件類別，並包含基本結構成員函式來初始化文件、序列化 (儲存和載入) 文件，以及實作偵錯診斷。|
|*Projname*set.h/.cpp|當您建立支援資料庫且包含資料錄集類別的程式時建立。|
|*Projname*view.cpp、*Projname*view.h|衍生和實作名為 `CProjnameView` 的檢視類別，用來顯示和列印文件資料。 `CProjnameView` 類別衍生自下列其中一個 MFC 類別：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 專案的檢視類別包含要繪製檢視並實作偵錯診斷的基本結構成員函式。 如果您已啟用列印支援，則會針對列印、列印設定以及列印預覽命令訊息新增訊息對應項目。 這些項目會在基底檢視類別中呼叫對應的成員函式。|
|*Projname*PropPage.h、*Projname*PropPage.cpp|宣告和實作 `CProjnamePropPage` 類別。 `CProjnamePropPage` 衍生自 `COlePropertyPage`，而且提供基本結構成員函式 `DoDataExchange` 來實作資料交換和驗證。|
|IPframe.cpp、IPframe.h|當在應用程式精靈的 [自動化選項] 頁面 (步驟 6 之 3) 中選取 [迷你伺服器] 或 [完整伺服器] 選項時建立。 這些檔案會衍生和實作名為 **CInPlaceFrame** 的就地框架視窗類別，容器程式就地啟用伺服器時會使用此類別。|
|Mainfrm.cpp、Mainfrm.h|從 [CFrameWnd](../mfc/reference/cframewnd-class.md) (適用於 SDI 應用程式) 或 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) (適用於 MDI 應用程式) 衍生 **CMainFrame** 類別。 如果在應用程式精靈的 [應用程式選項] 頁面 (步驟 6 之 4) 中選取對應的選項，**CMainFrame** 類別就會負責建立工具列按鈕和狀態列。 如需使用 **CMainFrame** 的資訊，請參閱[應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|
|Childfrm.cpp、Childfrm.h|從 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 衍生 **CChildFrame** 類別。 **CChildFrame** 類別用於 MDI 文件框架視窗。 如果您選取 MDI 選項，則一律會建立這些檔案。|

## <a name="see-also"></a>請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[ATL 程式或控制項原始程式檔和標頭檔](../ide/atl-program-or-control-source-and-header-files.md)<br>
[CLR 專案](../ide/files-created-for-clr-projects.md)