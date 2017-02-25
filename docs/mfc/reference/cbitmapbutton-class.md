---
title: "CBitmapButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBitmapButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "點陣圖, button controls"
  - "按鈕, 點陣圖"
  - "CBitmapButton class"
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CBitmapButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立按鈕控制項標記中的點陣圖影像來代替文字。  
  
## 語法  
  
```  
class CBitmapButton : public CButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBitmapButton::CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md)|建構 `CBitmapButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBitmapButton::AutoLoad](../Topic/CBitmapButton::AutoLoad.md)|關聯在對話方塊中的  按鈕的 `CBitmapButton` 類別的物件，以名稱載入點陣圖，並調整按鈕的相容的點陣圖。|  
|[CBitmapButton::LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md)|透過載入一或多個具名的點陣圖資源從應用程式的資源檔和附加點陣圖初始化物件至物件。|  
|[CBitmapButton::SizeToContent](../Topic/CBitmapButton::SizeToContent.md)|調整按鈕的大小以容納點陣圖。|  
  
## 備註  
 `CBitmapButton` 物件包含四個點陣圖，包含不同狀態影像按鈕可以假設:\(一般\)，向下 \(或選取\)，反白顯示並停用。  只需要第一個點陣圖，另一個是選擇性的。  
  
 點陣圖按鈕在影像以及影像周圍加上框線。  框線通常會在中顯示按鈕的狀態沒有作用。  例如，具有焦點的狀態的點陣圖通常是與這個狀態中，但這個邊界的虛線矩形內凹或是在迴實線框線。  處於停用狀態的點陣圖通常類似這個狀態中，但具有較低的對比 \(像暗灰色的或選取功能表\)。  
  
 這些點陣圖可以是任何大小，不過，所有，視為已相同大小的這個狀態的點陣圖。  
  
 各種應用程式需要點陣圖影像的不同組合:  
  
|向上鍵|向下|Focused|Disabled|應用程式|  
|---------|--------|-------------|--------------|----------|  
|×||||點陣圖|  
|×|×|||沒有 **WS\_TABSTOP** 模式的按鈕|  
|×|×|×|×|對話方塊按鈕的所有狀態。|  
|×|×|×||具有 **WS\_TABSTOP** 樣式的對話方塊按鈕|  
  
 當建立點陣圖按鈕控制項，請將 **BS\_OWNERDRAW** 樣式指定擁有者繪製按鈕。  這會導致視窗傳送按鈕的 `WM_MEASUREITEM` 和 `WM_DRAWITEM` 資訊;這個架構處理這些訊息並處理按鈕的外觀。您的。  
  
### 建立在視窗工作區的點陣圖按鈕控制項  
  
1.  建立按鈕的一到四個點陣圖影像。  
  
2.  [CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md) 建構物件。  
  
3.  呼叫 [建立](../Topic/CButton::Create.md) 函式建立 Windows 按鈕控制項並將它附加至 `CBitmapButton` 物件。  
  
4.  在點陣圖按鈕建構完成後，請呼叫成員函式 [LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md) 載入點陣圖資源。  
  
### 包含點陣圖按鈕控制對話方塊  
  
1.  建立按鈕的一到四個點陣圖影像。  
  
2.  建立具有所在的主控描繪 \(Owner\-Drawn\) 按鈕的對話方塊範本所需的點陣圖按鈕的位置。  按鈕的大小在範本並不重要。  
  
3.  將按鈕的標頭設定為指定的值 \(例如「**MYIMAGE**」並定義按鈕的符號 \(例如 **IDC\_MYIMAGE**。  
  
4.  在應用程式的資源指令碼，請重新命名為按鈕建立的每個影像附加建構之 ID 的其中一個字母「U，」， 「D」、「，」或「X」\(，下，反白顯示，並停用\) 則按鈕標題的字串在步驟 3. 步驟。  對於按鈕標題「**MYIMAGE**」，例如， ID 為「，」**MYIMAGEU**「**MYIMAGED**」，**MYIMAGEF**「，以及」**MYIMAGEX**」。您 **must** 指定放置在雙引號內的點陣圖 ID。  否則資源編輯器會將整數至資源，而 MFC 會失敗，在載入影像時。  
  
5.  在應用程式中的對話方塊類別 \(衍生自 `CDialog`\) 中，加入 `CBitmapButton` 成員物件。  
  
6.  在 `CDialog` 物件的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 常式，請呼叫 `CBitmapButton` 物件的 [自動載入](../Topic/CBitmapButton::AutoLoad.md) 函式，使用參數，按鈕的控制項 ID 和 `CDialog` 物件的 **this** 指標。  
  
 如果您想要處理 Windows 訊息，告知 \(例如， **BN\_CLICKED**送出的點陣圖按鈕於其父控制項 \(通常是從 **CDialog\)**衍生自類別的類別，加入至 `CDialog`衍生物件的每個訊息的訊息對應項目和訊息處理常式成員函式。  `CBitmapButton` 物件傳送的告知數目相同。 [CButton](../../mfc/reference/cbutton-class.md) 物件傳送的項目。  
  
 類別 [CToolBar](../../mfc/reference/ctoolbar-class.md) 接受各種不同的方法加入點陣圖按鈕。  
  
 如需 `CBitmapButton`的資訊，請參閱[控制項](../../mfc/controls-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 CTRLTEST](../../top/visual-cpp-samples.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)