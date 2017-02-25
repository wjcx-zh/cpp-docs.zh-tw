---
title: "關閉可見時啟動選項 | Microsoft Docs"
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
  - "MFC ActiveX 控制項 [C++], 啟動選項"
  - "可見時啟動選項"
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 關閉可見時啟動選項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制項有兩種基本的狀態:現用及非現用。  傳統上，這些狀態分別由是否具有視窗的控制項區別。  現用控制項具有視窗;非現用控制項沒有。  無視窗啟動的簡介，這分別不再是通用的，不過仍適用於許多控制項。  
  
 比較 ActiveX 控制項通常會執行初始化的其餘部分，視窗的建立是非常耗費資源的作業。  在理想狀況下，控制項會延後建立其除非絕對必要的視窗。  
  
 會在容器中可見許多控制項不需要為作用中。  通常，控制項在非現用狀態可能中，直到使用者執行例如要求它成為使用中的作業 \(按一下滑鼠或按下 TAB 鍵\)。  若要使控制項維持在非作用狀態直到容器需要啟動它，從控制項的其他旗標移除 **OLEMISC\_ACTIVATEWHENVISIBLE** 旗標:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/CPP/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC\_ACTIVATEWHENVISIBLE** 旗標會自動被省略，則關閉在 MFC ActiveX 控制項精靈的 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面 **Activate When Visible** 選項，當您建立控制項時。  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)