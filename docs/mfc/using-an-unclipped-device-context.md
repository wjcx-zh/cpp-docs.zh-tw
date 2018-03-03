---
title: "使用未裁剪的裝置內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae095b59b07132bd7e4c6892b8e58d9e69fb39c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-unclipped-device-context"></a>使用未裁剪的裝置內容
如果您完全確定您的控制項不會繪製到其用戶端矩形之外，您也可以停用 `IntersectClipRect` 所進行的 `COleControl` 呼叫，以獲得小而可偵測的速度增益。 若要這樣做，請移除**colecontrol:: Getcontrolflags**集中所傳回的旗標的旗標[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如:   
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 如果您選取要移除這個旗標的程式碼會自動產生**未裁剪的裝置內容**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面上，使用 [MFC ActiveX 控制項精靈] 建立控制項時。  
  
 如果您使用無視窗啟用，這個最佳化不會有作用。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

