---
title: 使用 CAnimateCtrl |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5685d6aed00cd57f4329b3865f96fa75226d7cf6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-canimatectrl"></a>使用 CAnimateCtrl
動畫控制項，此類別所代表[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)，是一種視窗中音訊視訊交錯格式 (AVI) 格式顯示剪輯-標準的 Windows 視訊與音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。  
  
 因為在播放 AVI 短片的同時，您的執行緒會繼續執行，因此動畫控制項的常見用法之一是在長時間作業期間表示系統的活動。 例如，[Windows 搜尋] 對話方塊會隨著系統搜尋檔案而顯示一個移動的放大鏡。  
  
 動畫控制項只能播放簡單的 AVI 短片，且不支援音效 (如需完整的限制清單，請參閱[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)。)由於動畫控制項的功能受到嚴格的限制且隨時可能會變更，因此您應該使用替代方法，例如，若您需要控制項提供多媒體播放和/或記錄功能，請使用 MCIWnd 控制項。 如需 MCIWnd 控制項的詳細資訊，請參閱多媒體文件。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [使用動畫控制項](../mfc/using-an-animation-control.md)  
  
-   [動畫控制項傳送的通知](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>另請參閱  
 [控制項](../mfc/controls-mfc.md)

