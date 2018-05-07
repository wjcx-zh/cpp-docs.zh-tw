---
title: 啟用工具提示 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 598583360eca2a65a5352fc9d284d8d359ac021c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-tool-tips"></a>啟用工具提示
您可以讓工具提示支援視窗的子控制項 (例如在表單檢視或對話方塊的控制項)。  
  
### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>為視窗的子控制項啟用工具提示  
  
1.  對於您想提供工具提示的視窗，呼叫視窗的 `EnableToolTips`。  
  
2.  在每個控制項提供字串您[TTN_NEEDTEXT 告知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)處理常式。 處理常式是在包含子控制項視窗的訊息對應中 (例如，您的表單檢視類別)。 這個處理常式應該所呼叫的函式識別控制項並設定**pszText**指定工具提示控制項所使用的文字。  
  
## <a name="see-also"></a>另請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

