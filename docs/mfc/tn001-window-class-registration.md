---
title: "TN001：視窗類別註冊 | Microsoft Docs"
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
  - "vc.registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterClass 函式"
  - "TN001"
  - "WNDCLASS"
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN001：視窗類別註冊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註描述註冊 Windows、所需的特殊 [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)的 MFC 常式。  MFC 使用的特定 `WNDCLASS` 屬性和 Windows 討論。  
  
## 問題  
 [CWnd](../mfc/reference/cwnd-class.md) 屬性的物件，就像在 Windows 中的 `HWND` 控制代碼，存在兩個位置中: 視窗物件和 `WNDCLASS`。  `WNDCLASS` 的名稱傳遞至一般視窗建立函式，例如 [CWnd::Create](../Topic/CWnd::Create.md) 和 [CFrameWnd::Create](../Topic/CFrameWnd::Create.md) 中 `lpszClassName` 參數。  
  
 必須透過四種方式之一來註冊此 `WNDCLASS` :  
  
-   隱含使用 MFC 所提供的 `WNDCLASS`。  
  
-   隱含地透過子類別化視窗控制項 \(或其他控制項\)。  
  
-   明確呼叫 MFC [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 或 [AfxRegisterClass](../Topic/AfxRegisterClass.md)。  
  
-   明確呼叫 Windows 常式 [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586)。  
  
## WNDCLASS 欄位  
 `WNDCLASS` 結構包含描述一個視窗類別的各種欄位。  下表顯示欄位並指定如何在 MFC 應用程式使用它們:  
  
|欄位|說明|  
|--------|--------|  
|`lpfnWndProc`|視窗程序，必須是 `AfxWndProc`|  
|`cbClsExtra`|不被使用\(應該為零\)。|  
|`cbWndExtra`|不被使用\(應該為零\)。|  
|`hInstance`|用 [AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)自動填入|  
|`hIcon`|框架視窗的圖示，請參閱以下|  
|`hCursor`|當滑鼠在視窗時的游標，請參閱以下|  
|`hbrBackground`|背景色彩，請參閱以下|  
|`lpszMenuName`|不被使用\(應該為空\)。|  
|`lpszClassName`|類別名稱，請參閱以下|  
  
## 提供的 WNDCLASSes  
 MFC 舊版 \(在 MFC 4.0\) 之前，提供數個預先定義視窗類別。  預設不再提供這些視窗類別。  應用程式應該使用適當參數的 `AfxRegisterWndClass` 。  
  
 如果應用程式的資源以指定的資源 ID \(例如， AFX\_IDI\_STD\_FRAME\)， MFC 會使用該資源。  否則會使用預設資源。  對於圖示，使用標準應用程式圖示，對於游標，使用標準箭號游標。  
  
 兩個圖示支援與單一文件類型的 MDI 應用程式: 主應用程式的圖示，圖示文件\/MDIChild 視窗的另一個圖示。  如果是以不同的圖示的多個資料型別，您必須註冊其他 `WNDCLASS`、或使用 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 函式。  
  
 `CFrameWnd::LoadFrame` 會註冊 `WNDCLASS` 使用您指定為第一個參數和下列標準屬性的圖示 ID:  
  
-   類別樣式：CS\_DBLCLKS&#124;CS\_HREDRAW&#124;CS\_VREDRAW;  
  
-   圖示 AFX\_IDI\_STD\_FRAME  
  
-   鍵頭游標。  
  
-   COLOR\_WINDOW 背景色彩  
  
 背景色彩的 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 值和游標，因為 `CMDIFrameWnd` 的工作區是由包含於 \[**MDICLIENT**\] 視窗。  Microsoft 不鼓勵子類別化 \[**MDICLIENT**\] 視窗，因此請使用標準色彩和資料指標型別。  
  
## 子類別化和 Superclassing 控制項  
 如果您的子類別或 Superclass 的 Windows 控制項 \(例如 [CButton](../mfc/reference/cbutton-class.md)\)，所以您的類別在該控制項提供的 Windows 實作自動取得 `WNDCLASS` 屬性。  
  
## AfxRegisterWndClass 函式  
 MFC 提供 Helper 函式來註冊視窗類別。  將一組屬性 \(視窗的類別樣式、游標、背景筆刷和圖示\)，產生綜合名稱，且註冊產生的視窗類別。  例如：  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle, HCURSOR hCursor, HBRUSH hbrBackground, HICON hIcon);  
```  
  
 這個函式會傳回產生的註冊視窗類別名稱的暫存資料。  如需這個函式的詳細資訊，請參閱[AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 。  
  
 傳回的字串是暫存指標在靜態字串緩衝區。  它是有效直到下一次呼叫 `AfxRegisterWndClass`。  如果您要此字串，請將它儲存在一個 [CString](../atl-mfc-shared/using-cstring.md) 變數，如下列範例所示:  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);  
...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);  
...  
```  
  
 `AfxRegisterWndClass` 會擲回 [CResourceException](../mfc/reference/cresourceexception-class.md) ，如果視窗類別未註冊 \(因為錯誤的參數，或在 Windows 記憶體之外\)。  
  
## RegisterClass 和 AfxRegisterClass 函式  
 如果您要比 `AfxRegisterWndClass` 提供更複雜的任何項目，您可以呼叫 Windows API `RegisterClass` 或 MFC 函式 `AfxRegisterClass`。  `CWnd`、`Create` [CFrameWnd](../mfc/reference/cframewnd-class.md) 和 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 函式採用 `lpszClassName` 字串名稱視窗類別做為第一個參數。  您可以使用任何已登錄的視窗類別名稱，不論您用來註冊其方法。  
  
 在 Win32 的 DLL 使用 `AfxRegisterClass` \(或 `AfxRegisterWndClass`\) 是重要的。  Win32 沒有自動 DLL 登錄移除註冊類別，因此，您需要明確移除註冊類別，當 DLL 結束時。  使用`AfxRegisterClass`而非`RegisterClass`，這會自動處理。  當 DLL 終止時，`AfxRegisterClass` 會維護您的 DLL 登錄的唯一類別清單並自動將移除它們。  當您在 DLL 時使用 `RegisterClass` ，您必須確定所有類別已移除註冊，當 DLL 終止時 \(在 [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) 函式\)。  當另一個用戶端應用程式嘗試使用您的 DLL 時，失敗可能造成 `RegisterClass` 未預期地失敗。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)