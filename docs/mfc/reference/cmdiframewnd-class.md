---
title: "CMDIFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWnd class"
  - "MDI frame windows"
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMDIFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

與成員一起提供 Windows 多重文件介面 \(MDI\) \(MDI\) 框架視窗的功能，用於管理視窗。  
  
## 語法  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMDIFrameWnd::CMDIFrameWnd](../Topic/CMDIFrameWnd::CMDIFrameWnd.md)|建構 `CMDIFrameWnd`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMDIFrameWnd::CreateClient](../Topic/CMDIFrameWnd::CreateClient.md)|建立這個 `CMDIFrameWnd`的視窗 **MDICLIENT** 視窗。  呼叫 `CWnd`的 `OnCreate` 成員函式。|  
|[CMDIFrameWnd::CreateNewChild](../Topic/CMDIFrameWnd::CreateNewChild.md)|建立新的子視窗。|  
|[CMDIFrameWnd::GetWindowMenuPopup](../Topic/CMDIFrameWnd::GetWindowMenuPopup.md)|傳回視窗的快顯功能表。|  
|[CMDIFrameWnd::MDIActivate](../Topic/CMDIFrameWnd::MDIActivate.md)|啟動不同的 MDI 子視窗。|  
|[CMDIFrameWnd::MDICascade](../Topic/CMDIFrameWnd::MDICascade.md)|排列重疊顯示格式的所有子視窗。|  
|[CMDIFrameWnd::MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md)|使用指示是否子系的旗標一起擷取目前作用中的 MDI 子視窗，最大化。|  
|[CMDIFrameWnd::MDIIconArrange](../Topic/CMDIFrameWnd::MDIIconArrange.md)|讓所有資料最小化的子視窗。|  
|[CMDIFrameWnd::MDIMaximize](../Topic/CMDIFrameWnd::MDIMaximize.md)|最大化 MDI 子視窗。|  
|[CMDIFrameWnd::MDINext](../Topic/CMDIFrameWnd::MDINext.md)|啟動子視窗位於目前作用中的子視窗之後而在其他子視窗後面加入目前作用中的子視窗。|  
|[CMDIFrameWnd::MDIPrev](../Topic/CMDIFrameWnd::MDIPrev.md)|啟動上一個子視窗並緊接在它後面加入目前作用中的子視窗。|  
|[CMDIFrameWnd::MDIRestore](../Topic/CMDIFrameWnd::MDIRestore.md)|還原最大化或最小化大小的 MDI 子視窗。|  
|[CMDIFrameWnd::MDISetMenu](../Topic/CMDIFrameWnd::MDISetMenu.md)|取代 MDI 框架視窗的功能表，視窗快顯功能表或兩者。|  
|[CMDIFrameWnd::MDITile](../Topic/CMDIFrameWnd::MDITile.md)|排列在並排顯示的格式的所有子視窗。|  
  
## 備註  
 若要建置應用程式的有用 MDI 框架視窗，請從 `CMDIFrameWnd`衍生一個類別。  將成員變數加入衍生類別加入儲存資料的特定應用程式。  實作的訊息處理常式 \(成員函式和訊息對應在衍生類別中指定的情形，當訊息導向至視窗。  
  
 您可以藉由呼叫 `CFrameWnd`的 [建立](../Topic/CFrameWnd::Create.md) 或 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 成員函式建構 MDI 框架視窗。  
  
 在呼叫或之前， **建立**`LoadFrame`使用 C\+\+ **new** 運算子，必須建構堆積中的框架視窗物件。   在呼叫之前 **建立** 也可以註冊類別的視窗。 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全域函式將框架的圖示和類別樣式。  
  
 使用 **建立** 成員函式是透過架構的建立參數做為直接引數。  
  
 `LoadFrame` 比 **建立**需要較少引數和從資源擷取其大部分預設值，包括框架的標題、圖示、快速鍵對應表和功能表。  將由 `LoadFrame`存取，這些資源必須具有相同的資源 ID \(例如， **IDR\_MAINFRAME**\)。  
  
 雖然 **MDIFrameWnd** 從 `CFrameWnd`衍生，框架視窗類別從 `CMDIFrameWnd` 衍生自不需要宣告 `DECLARE_DYNCREATE`。  
  
 `CMDIFrameWnd` 類別繼承自 `CFrameWnd`的預設實作。  如需使用這些功能的詳細清單，請參閱 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 類別描述。  `CMDIFrameWnd` 類別具有下列功能:  
  
-   MDI 框架視窗管理 **MDICLIENT** 視窗，變更其位置與控制項搭配使用。  MDI 用戶端視窗是 MDI 子框架視窗的直接上層父代。  在 `CMDIFrameWnd` 指定的 **WS\_HSCROLL** 和 **WS\_VSCROLL** 視窗樣式適用於 MDI 用戶端視窗而不是主框架視窗中，讓使用者可以捲動 MDI 工作區 \(例如在  視窗中項目的處理常式，\)。  
  
-   MDI 框架視窗擁有使用為功能表列的預設功能表，當沒有現用 MDI 子視窗時。  如果有作用中的 MDI 子系時， MDI 框架視窗的功能表列的 MDI 子視窗功能表自動取代。  
  
-   如果有的話， MDI 框架視窗與目前的 MDI 子視窗搭配運作。  例如，命令訊息委派至目前作用中的 MDI 子系，在 MDI 框架視窗之前。  
  
-   MDI 框架視窗具有下列標準視窗功能表命令的預設處理常式:  
  
    -   **ID\_WINDOW\_TILE\_VERT**  
  
    -   **ID\_WINDOW\_TILE\_HORZ**  
  
    -   **ID\_WINDOW\_CASCADE**  
  
    -   **ID\_WINDOW\_ARRANGE**  
  
-   MDI 框架視窗還有 **ID\_WINDOW\_NEW**的實作中，建立新的框架和檢視目前的文件。  應用程式可以覆寫這些預設值命令實作自訂的 MDI 視窗處理。  
  
 請不要使用 C\+\+ **刪除** 運算子終結框架視窗。  請改用 `CWnd::DestroyWindow`。  在終結， `PostNcDestroy` 的 `CFrameWnd` 實作要刪除 C\+\+ 物件視窗。  當使用者關閉框架視窗，預設 `OnClose` 管理員會呼叫 `DestroyWindow`。  
  
 如需 `CMDIFrameWnd`的資訊，請參閱 [框架視窗](../../mfc/frame-windows.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [MFC MDIDOCVW 範例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW 範例](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)