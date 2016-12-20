---
title: "CMDIChildWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIChildWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子視窗, CMDIChildWnd class"
  - "CMDIChildWnd class"
  - "MDI [C++], 子視窗"
  - "windows [C++], MDI"
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIChildWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

與成員一起提供 Window \(MDI\) 多重文件介面 \(MDI\) 子視窗的功能，用於管理視窗。  
  
## 語法  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMDIChildWnd::CMDIChildWnd](../Topic/CMDIChildWnd::CMDIChildWnd.md)|建構 `CMDIChildWnd` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMDIChildWnd::Create](../Topic/CMDIChildWnd::Create.md)|建立視窗 MDI 子視窗與 `CMDIChildWnd` 物件。|  
|[CMDIChildWnd::GetMDIFrame](../Topic/CMDIChildWnd::GetMDIFrame.md)|傳回 MDI 用戶端視窗的 MDI 父框架。|  
|[CMDIChildWnd::MDIActivate](../Topic/CMDIChildWnd::MDIActivate.md)|啟動這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIDestroy](../Topic/CMDIChildWnd::MDIDestroy.md)|終結這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIMaximize](../Topic/CMDIChildWnd::MDIMaximize.md)|最大化這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIRestore](../Topic/CMDIChildWnd::MDIRestore.md)|還原最大化或最小化大小之 MDI 子視窗。|  
|[CMDIChildWnd::SetHandles](../Topic/CMDIChildWnd::SetHandles.md)|將功能表和快速鍵資源控制代碼。|  
  
## 備註  
 MDI 子視窗看起來很像一般的框架視窗，不過， MDI 子視窗會出現在主框架視窗內 \(而不是在桌上型電腦執行。  MDI 子視窗沒有自己的功能表列，相反地，共用 MDI 框架視窗的功能表。  這個架構便會自動地變更 MDI 框架功能表表示目前現用 MDI 子視窗。  
  
 若要為應用程式建立一個有用的 MDI 子視窗， `CMDIChildWnd`從衍生一個類別。   將成員變數加入衍生類別加入儲存資料的特定應用程式。  實作的訊息處理常式 \(成員函式和訊息對應在衍生類別中指定的情形，當訊息導向至視窗。  
  
 有三種方式建構 MDI 子視窗:  
  
-   使用 **建立**，請直接建構它。  
  
-   使用 `LoadFrame`，請直接建構它。  
  
-   請將文件樣板間接建構它。  
  
 在呼叫或之前， **建立**`LoadFrame`使用 C\+\+ **new** 運算子，必須建構堆積中的框架視窗物件。    在呼叫之前 **建立** 也可以註冊類別的視窗。 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全域函式將框架的圖示和類別樣式。  
  
 使用 **建立** 成員函式是透過架構的建立參數做為直接引數。  
  
 `LoadFrame` 比 **建立**需要較少引數和從資源擷取其大部分預設值，包括框架的標題、圖示、快速鍵對應表和功能表。  若要存取由 `LoadFrame`，這些資源必須具有相同的資源 ID \(例如， **IDR\_MAINFRAME**\)。  
  
 當 `CMDIChildWnd` 物件包含檢視和文件時，便會由架構間接建立而不是直接由程式設計人員。   `CDocTemplate` 物件組織架構的建立，包含之檢視的建立和檢視的連結至適當的資料。  `CDocTemplate` 建構函式的參數指定涉及三個類別的 `CRuntimeClass` \(文件、架構和檢視\)。   這個架構可用來 `CRuntimeClass` 物件動態建立新的框架 \(Frame\)，指定由使用者 \(例如，藉由使用檔案的新命令或 MDI 視窗新命令\)。  
  
 必須宣告 `CMDIChildWnd` 從取得的框架視窗類別與 `DECLARE_DYNCREATE` 為了頂端 `RUNTIME_CLASS` 機制以正確地運作。  
  
 `CMDIChildWnd` 類別繼承自 `CFrameWnd`的預設實作。    如需使用這些功能的詳細清單，請參閱 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 類別描述。   `CMDIChildWnd` 類別具有下列功能:  
  
-   `CMultiDocTemplate` 與類別結合，多 `CMDIChildWnd` 從同一份文件樣板物件共用相同的功能表，儲存 Windows 系統資源。  
  
-   目前作用中的 MDI 子視窗功能表完全取代 MDI 框架視窗功能表，，且目前作用中的 MDI 子視窗的標頭加入至 MDI 框架視窗的標題。   如需 MDI 子表單在 MDI 框架視窗一起實作 Windows 函式的其他範例，請參閱 `CMDIFrameWnd` 類別描述。  
  
 請不要使用 C\+\+ **刪除** 運算子終結框架視窗。  請改用 `CWnd::DestroyWindow`。  在終結， `PostNcDestroy` 的 `CFrameWnd` 實作要刪除 C\+\+ 物件視窗。  當使用者關閉框架視窗，預設 `OnClose` 管理員會呼叫 `DestroyWindow`。  
  
 如需 `CMDIChildWnd`的資訊，請參閱 [框架視窗](../../mfc/frame-windows.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [MFC MDIDOCVW 範例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW 範例](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)