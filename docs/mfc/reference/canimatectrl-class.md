---
title: "CAnimateCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "animation controls [C++], CAnimateCtrl class"
  - "CAnimateCtrl class"
  - "Windows common controls [C++], CAnimateCtrl class"
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CAnimateCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用控制項動畫的功能。  
  
## 語法  
  
```  
  
class CAnimateCtrl : public CWnd  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimateCtrl::CAnimateCtrl](../Topic/CAnimateCtrl::CAnimateCtrl.md)|建構 `CAnimateCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimateCtrl::Close](../Topic/CAnimateCtrl::Close.md)|關閉 AVI 裁剪。|  
|[CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)|建立動畫控制項並將其附加至 `CAnimateCtrl` 物件。|  
|[CAnimateCtrl::CreateEx](../Topic/CAnimateCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的動畫控制項並將其附加至 `CAnimateCtrl` 物件。|  
|[CAnimateCtrl::IsPlaying](../Topic/CAnimateCtrl::IsPlaying.md)|表示音訊或視訊交錯 \(AVI\) 裁剪是否使用。|  
|[CAnimateCtrl::Open](../Topic/CAnimateCtrl::Open.md)|從  開啟檔案或資源的一個 AVI 底框並顯示第一個畫面格。|  
|[CAnimateCtrl::Play](../Topic/CAnimateCtrl::Play.md)|播放 AVI 裁剪，不含音效。|  
|[CAnimateCtrl::Seek](../Topic/CAnimateCtrl::Seek.md)|顯示 AVI 裁剪中所選取的單一框架。|  
|[CAnimateCtrl::Stop](../Topic/CAnimateCtrl::Stop.md)|停止播放 AVI 裁剪。|  
  
## 備註  
 這個控制項 \(也 `CAnimateCtrl` 類別\) 給在 Windows 95、Windows 98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 動畫控制項是顯示一個裁剪以 AVI 的矩形視窗 \(交錯音訊或視訊\) 格式標準 Windows 視訊和音訊格式。  AVI 底框是一連串點陣圖框架，就像電影。  
  
 動畫控制項只能用來播放簡單 AVI 裁剪。  特別是，動畫會使用控制項的底框必須符合下列需求:  
  
-   必須剛好有一個視訊資料流，且至少必須有一個框架。  
  
-   可以最多只有一個檔案中的兩個資料流 \(通常是另一個資料流，如果有的話，是音訊串流，不過，動畫控制項忽略音訊資訊\)。  
  
-   裁剪必須是未壓縮或解壓縮的使用 RLE8 壓縮。  
  
-   調色盤變更不允許在視訊資料流中。  
  
 您可以將 AVI 裁剪至您的應用程式為 AVI 資源，或是可以隨附的應用程式，可以在個別的 AVI 檔。  
  
 因為您的執行緒繼續執行，則 AVI 裁剪顯示時，常見用法之一是動畫控制項表示系統活動在長時間作業時。  例如，在中，當系統檔案中搜尋，尋找對話方塊檔案總管中會顯示一個移動的放大鏡。  
  
 使用對話方塊編輯器中，如果您建立了 `CAnimateCtrl` 物件在對話方塊內或在對話方塊資源，然後將自動終結它，當使用者關閉對話方塊。  
  
 如果您在視窗內的 `CAnimateCtrl` 物件，可能要終結它。  如果您在堆疊上建立物件， `CAnimateCtrl` 自動終結。  您可以使用 **new** 函式，建立。 `CAnimateCtrl` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結它。  如果您從 `CAnimateCtrl` 衍生新的類別並將該類別的任何記憶體，請覆寫 `CAnimateCtrl` 解構函式處理組態。  
  
 如需使用 `CAnimateCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)   
 [ON\_CONTROL](../Topic/ON_CONTROL.md)