---
title: "MFC 程式或控制項原始程式檔和標頭檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案類型 [C++], MFC 原始檔和檔頭檔"
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC 程式或控制項原始程式檔和標頭檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據您為所建立專案選取的選項，當您在 Visual Studio 中建立 MFC 專案時會建立下列檔案。  例如，只有在建立以對話方塊為架構的專案或類別時，您的專案才會包含 *Projname*dlg.cpp 和 *Projname*dlg.h 檔案。  
  
 這些檔案都是位於 *Projname* 目錄中，和 \[方案總管\] 中的標頭檔 \(.h 檔\) 資料夾或原始程式檔 \(.cpp 檔\) 資料夾。  
  
|檔案名稱|描述|  
|----------|--------|  
|*Projname*.h|程式或 DLL 的主包含檔，  它包含所有全域符號和其他標頭檔的 `#include` 指示詞。  它會從 `CWinApp` 衍生 `CPrjnameApp` 類別並宣告 `InitInstance` 成員 \(Member\) 函式。  對控制項來說，`CPrjnameApp` 類別是衍生自 `COleControlModule`。|  
|*Projname*.cpp|主程式原始程式檔，  它會建立 `CPrjnameApp` 類別 \(衍生自 `CWinApp`\) 的物件並覆寫 `InitInstance` 成員函式。<br /><br /> 對可執行檔來說，`CPrjnameApp::InitInstance` 有下列幾項功能：  註冊文件樣板 \(當做文件與檢視之間的連接\)、建立主框架視窗 \(Main Frame Window\) 以及建立空白文件 \(或是在應用程式的命令列引數中指定的話則開啟文件\)。<br /><br /> 對 DLL 和 ActiveX \(原來為 OLE\) 控制項來說，`CProjNameApp::InitInstance` 會藉由呼叫 `COleObjectFactory::RegisterAll` 以 OLE 來註冊控制項的 Object Factory，並呼叫 `AfxOLEInit`。  此外，還會使用 `CProjNameApp::ExitInstance` 成員函式呼叫 **AfxOleTerm** 以從記憶體卸載控制項。<br /><br /> 這個檔案也會藉由實作 `DllRegisterServer` 和 `DllUnregisterServer` 函式在 Windows 系統註冊資料庫中註冊和移除註冊控制項。|  
|*Projname*ctrl.h、*Projname*ctrl.cpp|宣告並實作 `CProjnameCtrl` 類別。  `CProjnameCtrl` 衍生自 `COleControl`，是定義來初始化、繪製及序列化 \(載入和儲存\) 控制項部分成員函式的基本架構實作。  也會定義訊息、事件及分派對應 \(Dispatch Map\)。|  
|*Projname*dlg.cpp、*Projname*dlg.h|在您選擇對話方塊架構的應用程式時建立。  這些檔案會衍生並實作名為 `CProjnameDlg` 的對話方塊類別，也會包含基本架構成員函式來初始化對話方塊和執行對話資料交換 \(Dialog Data Exchange，DDX\)。  您的 About 對話方塊類別也會置放在這些檔案中，而不是 *Projname*.cpp。|  
|Dlgproxy.cpp、Dlgproxy.h|在對話方塊架構程式中，主對話方塊之專案 Automation Proxy 類別的實作檔和標頭檔。  只有在選擇 Automation 支援的情況下才使用。|  
|*Projname*doc.cpp、*Projname*doc.h|衍生並實作名為 `CProjnameDoc` 的文件類別，同時包含基本架構成員函式來初始化文件、序列化 \(儲存和載入\) 文件以及實作偵錯診斷。|  
|*Projname*set.h\/.cpp|在您建立的程式支援資料庫和包含資料錄集 \(Recordset\) 類別的情況下建立。|  
|*Projname*view.cpp、*Projname*view.h|衍生並實作名為 `CProjnameView` 的檢視類別，這是用來顯示和列印文件資料。  `CProjnameView` 類別是衍生自下列任一 MFC 類別：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 專案的檢視類別包含基本架構成員函式來繪製檢視並實作偵錯診斷。  如果您啟用列印支援，則會為列印、列印設定及預覽列印等命令訊息 \(Command Message\) 加入訊息對應項 \(Message\-Map Entry\)。  這些項目會呼叫基底 \(Base\) 檢視類別中的對應成員函式。|  
|*Projname*PropPage.h、*Projname*PropPage.cpp|宣告並實作 `CProjnamePropPage` 類別。  `CProjnamePropPage` 衍生自 `COlePropertyPage`，同時會提供基本架構成員函式 `DoDataExchange` 來實作資料交換和驗證。|  
|IPframe.cpp、IPframe.h|在應用程式精靈的 \[Automation 選項\] 頁面選取 \[迷你伺服程式\] 或 \[完整伺服程式\] 選項時建立 \(步驟 3，共 6 個步驟\)。  這些檔案會衍生並實作名為 **CInPlaceFrame** 的就地框架視窗 \(Frame Window\) 類別，這是當容器 \(Container\) 程式就地啟動伺服程式時使用。|  
|Mainfrm.cpp、Mainfrm.h|從 [CFrameWnd](../mfc/reference/cframewnd-class.md) \(SDI 應用程式\) 或 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) \(MDI 應用程式\) 衍生 **CMainFrame** 類別，  如果在應用程式精靈的 \[應用程式選項\] 頁面選取對應選項 \(步驟 4，共 6 個步驟\) 的話，**CMainFrame** 類別會處理工具列按鈕和狀態列的建立。  如需使用 **CMainFrame** 的詳細資訊，請參閱[應用程式精靈建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|  
|Childfrm.cpp、Childfrm.h|從 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 衍生 **CChildFrame** 類別，  **CChildFrame** 類別是用於 MDI 文件框架視窗。  如果您選取 MDI 選項，則一定會建立這些檔案。|  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [ATL 程式或控制項原始程式檔和標頭檔](../ide/atl-program-or-control-source-and-header-files.md)   
 [CLR 專案](../ide/files-created-for-clr-projects.md)