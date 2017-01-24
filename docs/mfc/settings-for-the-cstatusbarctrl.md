---
title: "CStatusBarCtrl 的設定 | Microsoft Docs"
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
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl 類別, 設定"
  - "狀態列控制項, 設定"
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatusBarCtrl 的設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) 狀態視窗的預設位置是在父視窗的底部，不過，您可以指定 `CCS_TOP` 樣式讓它出現在父視窗的工作區頂端。  
  
 您可以指定 **SBARS\_SIZEGRIP** 樣式以包含處於 `CStatusBarCtrl` 狀態視窗右端的調整大小的底框。  調整大小的底框類似縮放框線;它是使用者可以按一下並拖曳調整父視窗的矩形區域。  
  
> [!NOTE]
>  如果您合併 `CCS_TOP` 和 **SBARS\_SIZEGRIP** 樣式，產生的調整大小的底框不會作用，即使系統繪製在狀態視窗。  
  
 狀態視窗的視窗程序會自動設定控制項的初始大小和位置。  這個寬度與父視窗的使用者工作區相同。  高度根據目前選取到狀態視窗的裝置內容的字型的度量資訊和視窗框線寬度。  
  
 視窗程序會自動調整狀態視窗的大小，當收到 `WM_SIZE` 訊息。  通常，當父視窗大小變更時，父代 `WM_SIZE` 傳送資訊到狀態視窗。  
  
 您可以藉由呼叫 [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md)設定狀態視窗的繪圖區域的最小高度，指定最小高度 \(以像素為單位\)。  繪圖區域不包括視窗框線。  
  
 您可以呼叫 [GetBorders](../Topic/CStatusBarCtrl::GetBorders.md)擷取狀態視窗的框線寬度。  此成員函式包含接收水平框線，垂直框線和三角形邊界的寬度的指標。  
  
## 請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)