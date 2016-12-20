---
title: "MFC ActiveX 控制項：子類別化 Windows 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "precreatewindow"
  - "IsSubclassed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoSuperclassPaint 方法"
  - "IsSubclassed 方法"
  - "MFC ActiveX 控制項, 建立"
  - "MFC ActiveX 控制項, 子類別控制項"
  - "OnDraw 方法, MFC ActiveX 控制項"
  - "PreCreateWindow 方法, 覆寫"
  - "反映訊息, 在 ActiveX 控制項中"
  - "子類別化"
  - "子類別化 Windows 控制項"
  - "子類別化, Windows 控制項"
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：子類別化 Windows 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明子類別化通用 Windows 控制流程建立 ActiveX 控制項。  子類別化現有 Windows 控制項能夠快速開發 ActiveX 控制項。  新的控制項會有子視窗控制項的能力，例如繪製和回應滑鼠點選動作。  MFC ActiveX 控制項範例是 [按鈕](../top/visual-cpp-samples.md) 主要視窗控制項的範例。  
  
 對的子類別 Windows 控制項，完成下列工作:  
  
-   [覆寫 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成員函式](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [修改 OnDraw 成員函式](#_core_modifying_the_ondraw_member_function)  
  
-   [處理所有 ActiveX 控制項的訊息 \(OCM\) 會反映控制項](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  使用在 **Control Settings** 頁面，，的 **Select Parent Window Class** 下拉式清單中，如果您選取控制項子類別化這個工作為您完成由 ActiveX 控制項精靈。  
  
 請參閱知識庫 \(Knowledge Base\) Q243454 有關子類別化控制項的詳細資訊。  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> 覆寫 IsSubclassedControl 和 PreCreateWindow  
 若要覆寫 `PreCreateWindow` 和 `IsSubclassedControl`，將下列程式碼加入至控制項類別宣告的 `protected` 區段:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 在控制項實作檔 \(.CPP\) 中，加入下列程式碼會實作兩個覆寫的函式:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 請注意，在此範例中， Windows 按鈕控制項在 `PreCreateWindow`所指定。  不過，所有標準 Windows 控制項子類別化。  如需標準 Windows 控制項的詳細資訊，請參閱 [控制項](../mfc/controls-mfc.md)。  
  
 當子類別化 Windows 控制項，您可能會想要指定特定視窗樣式時 \(**WS\_**\) 或延伸視窗樣式 \(**WS\_EX\_**\) 旗標用於建立主控視窗。  您可以修改 **cs.style** 和 **cs.dwExStyle** 結構欄位可以這些參數的值在 `PreCreateWindow` 成員函式。  應使用 `OR` 作業，這些欄位的修改，保存由類別 `COleControl`設定的預設旗標。  例如，在中，如果控制項子類別化按鈕控制項，而且想要控制項顯示為核取方塊，請將下列程式碼插入至 `CSampleCtrl::PreCreateWindow`的實作，在 return 陳述式之前:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 此作業將 **BS\_CHECKBOX** 樣式旗標，，讓預設樣式旗標 \(**WS\_CHILD**\) 類別 `COleControl` 不變。  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> 修改 OnDraw 成員函式  
 如果您希望子類別化控制項保留與對應的 Windows 控制項，控制項的 `OnDraw` 成員函式應該只包含呼叫 `DoSuperclassPaint` 成員函式的外觀，如下列範例所示:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 `DoSuperclassPaint` 成員函式，實作 `COleControl`，以指定之裝置內容的 Windows 控制項的視窗程序繪製控制項，在周框之內。  即使不是作用中，這樣可讓控制項成為可見。  
  
> [!NOTE]
>  `DoSuperclassPaint` 成員函式只會啟用裝置內容以 `WM_PAINT` 訊息的 **wParam** 的控制項型別一起使用。  這包括一些標準 Windows 控制項，例如 **SCROLLBAR** 和 **BUTTON**和所有通用控制項。  對於不支援這個行為的控制項，您必須提供自己的程式碼正確顯示非現用控制項。  
  
##  <a name="_core_handling_reflected_window_messages"></a> 處理反映的 Windows 訊息。  
 視窗控制項通常會將某些視窗訊息傳送給其父視窗。  這些訊息，例如 **WM\_COMMAND**，由使用者提供動作的通知。  其他選項，例如 `WM_CTLCOLOR`，用來取得父視窗的資訊。  ActiveX 控制項與父視窗通常通訊透過其他方法。  通知由引發事件傳送 \(傳送事件通知\)，以及控制項容器的資訊可以存取容器的環境屬性取得。  由於這些通訊技術存在， ActiveX 控制項容器不會處理控制項所傳送的任何視窗訊息。  
  
 若要防止容器接收子視窗控制項傳送 Windows 訊息， `COleControl` 建立額外的視窗做為控制項的父代。  這個額外的視窗，稱為「反映程式」，為的子類別視窗控制項的 ActiveX 控制項只會有相同的大小和位置與視窗控制項。  反映程式視窗攔截特定 Windows 訊息並將其加入至控制項。  控制項，在其視窗程序，可以採取動作然後處理這些反映訊息適用於 ActiveX 控制項 \(例如，引發事件\)。  為已攔截視窗訊息及其對應的反映訊息清單參閱 [要反映的 Windows 訊息 ID](../mfc/reflected-window-message-ids.md) 。  
  
 ActiveX 控制項容器可能會執行訊息反映，不需要 `COleControl` 建立反映程式視窗和減少子視窗控制項的執行階段的額外負荷。  `COleControl` 偵測容器是否可以核取支援這項功能 MessageReflect 環境屬性與 **TRUE**的值。  
  
 處理反映的 Windows 訊息，將項目加入至控制項資訊對應和實作處理函式。  由於反映訊息不是標準的部分 Windows 定義的訊息，類別檢視不支援將這類訊息處理常式。  不過，手動加入處理常式不困難。  
  
 若要將反映的 Windows 訊息的訊息處理常式手動執行下列動作:  
  
-   在控制項類別。.H 檔案，宣告處理常式函式。  函式應該具有 **LRESULT** 和兩個參數的傳回型別，而型別分別為 **WPARAM** 和 **LPARAM**。  例如：  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   在控制項類別 .CPP 檔案，請將 `ON_MESSAGE` 項目加入至訊息對應。  這個輸入參數應該是訊息識別項和處理常式函式的名稱。  例如：  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   因此在 .CPP 檔案，請實作 **OnOcmCommand** 成員函式處理反映訊息。  **wParam** 和 **lParam** 參數與原始的 Windows 訊息。  
  
 如需範例的反映訊息如何管理，請參閱 MFC ActiveX 控制項範例 [按鈕](../top/visual-cpp-samples.md)。  它會偵測 **BN\_CLICKED** 通知程式碼並透過引發的 **OnOcmCommand** 處理常式 \(傳送\) 回應點擊事件。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)