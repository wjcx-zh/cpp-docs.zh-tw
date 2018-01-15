---
title: "進度控制項的樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6186372dc3ac8bc1000a71706971c9ff72078c5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="styles-for-the-progress-control"></a>進度控制項的樣式
當您一開始建立進度控制項 ([cprogressctrl:: Create](../mfc/reference/cprogressctrl-class.md#create))，使用`dwStyle`參數來指定進度控制項的所需的視窗樣式。 下列清單詳細說明了適用的視窗樣式。 控制項會忽略除了此清單所列以外的所有視窗樣式。 您必須將控制項建立為子視窗，通常會以對話方塊為父代。  
  
|視窗樣式|作用|  
|------------------|------------|  
|`WS_BORDER`|在視窗周圍建立框線。|  
|**WS_CHILD**|建立子視窗 (應永遠為 `CProgressCtrl` 所使用)。|  
|**WS_CLIPCHILDREN**|在父視窗內繪圖時，應排除子視窗佔用的區域。 用於當您建立父視窗。|  
|**WS_CLIPSIBLINGS**|裁剪相對於彼此的子視窗。|  
|**WS_DISABLED**|建立一個一開始即停用的視窗。|  
|**WS_VISIBLE**|建立一個一開始即可見的視窗。|  
|**WS_TABSTOP**|指定控制項在使用者按下 TAB 鍵並移至它時可以接收焦點。|  
  
 此外，您可以指定兩個只適用於進度控制項的樣式 (`PBS_VERTICAL` 和 `PBS_SMOOTH`)。  
  
 使用 `PBS_VERTICAL` 垂直放置控制項，而非水平。 使用 `PBS_SMOOTH` 完全填滿控制項，而不是顯示重複填滿控制項的小方塊。  
  
 沒有 `PBS_SMOOTH` 樣式：  
  
 ![標準進度列樣式](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 有 `PBS_SMOOTH` 和 `PBS_VERTICAL` 樣式：  
  
 ![進度列的樣式、 平滑和垂直](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 如需詳細資訊，請參閱[視窗樣式](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc)中*MFC 參考*。  
  
## <a name="see-also"></a>請參閱  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)

