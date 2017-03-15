---
title: "MFC ActiveX 控制項：最佳化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "裝置內容, MFC ActiveX 控制項未裁剪的"
  - "避免重繪閃動的 ActiveX 控制項"
  - "MFC ActiveX 控制項, 現用/非現用狀態"
  - "MFC ActiveX 控制項, 避免重繪閃動的"
  - "MFC ActiveX 控制項, 滑鼠互動"
  - "MFC ActiveX 控制項, 最佳化"
  - "MFC ActiveX 控制項, 無視窗"
  - "最佳化, ActiveX 控制項"
  - "最佳化效能, ActiveX 控制項"
  - "效能, ActiveX 控制項"
  - "無視窗 MFC ActiveX 控制項"
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：最佳化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明可以使用最佳化效能較好的 ActiveX 控制項的技術。  
  
 主題 [關閉時，會啟動可見的選項](../mfc/turning-off-the-activate-when-visible-option.md) 和 [提供滑鼠互動，而非作用中](../mfc/providing-mouse-interaction-while-inactive.md) 討論不建立之前啟動的視窗的控制項。  這個主題 [提供無視窗啟動](../mfc/providing-windowless-activation.md) 討論未建立視窗的控制項，即使它們被啟動。  
  
 視窗具有 OLE 物件的兩個主要缺點:，表示現用和它們將大型負荷加入控制項時，會將它們顯示防止物件透明或非矩形。  通常，建立視窗所需控制項的建立時間的 60。  單一共用的視窗 \(通常是容器的\) 和特定排程器程式碼，控制取得相同的 Windows 服務，一般而言，不用效能損失。  在 Windows 中是物件的主要不必要的負荷。  
  
 當控制項在某些容器時，某些最佳化不一定改善效能。  例如，在 1996 之前釋放的容器不支援無視窗啟動，因此，實作這個功能不會提供較舊的容器的好處。  不過，幾乎每個容器支援持續性，因此，最佳化控制項繼續程式碼可能會改善其在所有容器的效能。  如果控制項特別適合用於容器的特定型別，您可能想要研究的最佳化該容器支援。  不過，一般而言，您應該嘗試實作許多技術與適用於您的特定控制項相同的很好確定您的控制項，就像它在多數容器可以。  
  
 您可以透過 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)實作許多這些最佳化，在 [控制項設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 頁面。  
  
### MFC ActiveX 控制項精靈、OLE 最佳化選項  
  
|控制項在 MFC ActiveX 控制項精靈的設定|動作|詳細資訊|  
|-------------------------------|--------|----------|  
|**Activate when visible** 核取方塊。|Clear|[關閉可見時啟動選項](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**Windowless activation** 核取方塊。|選取|[提供無視窗啟用](../mfc/providing-windowless-activation.md)|  
|**Unclipped device context** 核取方塊。|選取|[使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)|  
|**Flicker\-free activation** 核取方塊。|選取|[提供避免重繪閃動](../mfc/providing-flicker-free-activation.md)|  
|**當非現用時之滑鼠指標告知**核取方塊|選取|[非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Optimized drawing code** 核取方塊。|選取|[最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)|  
  
 如需這個成員的詳細資訊函式實作這些最佳化，請參閱 [COleControl](../mfc/reference/colecontrol-class.md)。  成員函式會使用清單，例如 [無視窗的作業](http://msdn.microsoft.com/zh-tw/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) 和 [非現用指標處理函式](http://msdn.microsoft.com/zh-tw/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)。  
  
 如需詳細資訊，請參閱：  
  
-   [最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [提供無視窗啟用](../mfc/providing-windowless-activation.md)  
  
-   [關閉可見時啟動選項](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [提供避免重繪閃動](../mfc/providing-flicker-free-activation.md)  
  
-   [使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)  
  
-   [最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)