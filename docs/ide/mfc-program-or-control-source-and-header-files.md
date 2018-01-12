---
title: "MFC 程式或控制項原始檔和標頭檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adb4ba4fdcc141438b2eeb87b4e3c9151bb9a5c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC 程式或控制項原始程式檔和標頭檔
當您建立 MFC 專案在 Visual Studio 中，根據您選取您建立專案的選項時，會建立下列檔案。 例如，您的專案包含*Projname*dlg.cpp 和*Projname*dlg.h 檔案，只有當您建立對話方塊架構的專案或類別。  
  
 所有這些檔案位於*Projname*目錄下，而標頭檔 （.h 檔案） 的資料夾或方案總管 中的原始程式檔 （.cpp 檔） 資料夾中。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|*Projname*.h|主要的 include 程式或 DLL 檔。 它包含所有全域符號和`#include`其他標頭檔的指示詞。 它衍生`CPrjnameApp`類別從`CWinApp`並宣告`InitInstance`成員函式。 控制項，`CPrjnameApp`類別衍生自`COleControlModule`。|  
|*Projname*.cpp|主要原始程式檔。 它會建立一個物件類別的`CPrjnameApp`，其衍生自`CWinApp`，並覆寫`InitInstance`成員函式。<br /><br /> 針對可執行檔，`CPrjnameApp::InitInstance`會執行數個。 它會註冊文件範本，做為文件和檢視; 之間的連線建立主框架視窗。並建立空的文件 （或開啟文件，如果其中一個指定為應用程式的命令列引數）。<br /><br /> 針對 Dll 和 ActiveX (先前稱為 OLE) 控制項，`CProjNameApp::InitInstance`向 OLE 註冊控制項的物件 factory，藉由呼叫`COleObjectFactory::RegisterAll`及會呼叫`AfxOLEInit`。 此外，此成員函式`CProjNameApp::ExitInstance`用來卸除從記憶體呼叫控制項**AfxOleTerm**。<br /><br /> 這個檔案也會註冊和取消註冊 Windows 系統註冊資料庫中的控制項，藉由實作`DllRegisterServer`和`DllUnregisterServer`函式。|  
|*Projname*ctrl.h， *Projname*ctrl.cpp|宣告和實作`CProjnameCtrl`類別。 `CProjnameCtrl`衍生自`COleControl`，以及一些成員函式的基本架構實作定義的初始化、 繪製和序列化 （載入及儲存） 控制項。 也會定義訊息、 事件和分派對應。|  
|*Projname*dlg.cpp， *Projname*dlg.h|如果您選擇對話方塊架構應用程式，建立。 衍生的檔案，以及實作名為的對話方塊類別`CProjnameDlg`，而且包含基本架構的成員函式來初始化的對話方塊，並執行對話方塊資料交換 (DDX)。 關於對話方塊類別也會放在這些檔案，而不是在*Projname*.cpp。|  
|Dlgproxy.cpp Dlgproxy.h|在對話方塊架構程式、 實作和標頭檔案中專案的主對話方塊的 Automation proxy 類別。 若您已選擇自動化支援時，這只會用於。|  
|*Projname*doc.cpp， *Projname*doc.h|衍生並實作的文件類別，名為`CProjnameDoc`，而且包含基本架構的成員函式來初始化文件、 序列化 （儲存和載入） 文件和偵錯診斷的實作。|  
|*Projname*set.h/.cpp|如果您建立支援資料庫，其中包含資料錄集類別的程式，建立。|  
|*Projname*view.cpp， *Projname*view.h|衍生並實作名為的檢視類別`CProjnameView`，用來顯示和列印文件資料。 `CProjnameView`類別衍生自下列的 MFC 類別的其中一個：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 專案的檢視類別包含要繪製的檢視和實作偵錯診斷的基本架構的成員函式。 如果您已啟用列印的支援，訊息對應項目已新增以列印、 列印設定，並列印預覽命令訊息。 這些項目在基底檢視類別中呼叫對應的成員函式。|  
|*Projname*PropPage.h， *Projname*PropPage.cpp|宣告和實作`CProjnamePropPage`類別。 `CProjnamePropPage`衍生自`COlePropertyPage`和基本架構的成員函式， `DoDataExchange`，提供給實作資料交換和驗證。|  
|IPframe.cpp IPframe.h|如果應用程式精靈中選取了迷你伺服器或完整伺服器 選項建立**自動化選項**頁面 （步驟 3 的 6）。 衍生的檔案，以及實作就地編輯框架視窗類別，名為**CInPlaceFrame**，就地啟用容器程式的伺服器時使用。|  
|Mainfrm.cpp Mainfrm.h|衍生**CMainFrame**類別從其中[CFrameWnd](../mfc/reference/cframewnd-class.md) （適用於 SDI 應用程式） 或[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) （對於 MDI 應用程式）。 **CMainFrame**類別會負責建立工具列按鈕和 [狀態] 列中，如果應用程式精靈中選取對應的選項**應用程式選項**頁面 （步驟 4 的 6）。 如需使用**CMainFrame**，請參閱[框架視窗類別建立應用程式精靈](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|  
|Childfrm.cpp Childfrm.h|衍生**CChildFrame**類別從[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。 **CChildFrame**類別用於 MDI 文件框架視窗。 如果您選取 MDI 選項，一律會建立這些檔案。|  
  
## <a name="see-also"></a>請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [ATL 程式或控制項原始檔和標頭檔](../ide/atl-program-or-control-source-and-header-files.md)   
 [CLR 專案](../ide/files-created-for-clr-projects.md)