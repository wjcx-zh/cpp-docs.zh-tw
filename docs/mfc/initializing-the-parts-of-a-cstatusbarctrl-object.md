---
title: 初始化 CStatusBarCtrl 物件的組件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89cea1516924530f821003affd96e2848687882b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344333"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>初始化 CStatusBarCtrl 物件的組件
根據預設，狀態列會使用不同的窗格顯示狀態資訊。 這些窗格 (也稱為組件) 可以包含文字字串、圖示或兩者。  
  
 使用[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)若要定義多少組件和長度，狀態列會有。 建立狀態列的組件之後，請呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)和[SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon)設定的文字或圖示的 [狀態] 列的特定部分。 成功設定組件後，會自動重新繪製控制項。  
  
 下列範例會初始化具有四個窗格的現有 `CStatusBarCtrl` 物件 (`m_StatusBarCtrl`)，然後在第二個組件中設定圖示 (IDI_ICON1) 和一些文字。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 如需有關設定的模式`CStatusBarCtrl`簡單，請參閱物件[設定 CStatusBarCtrl 物件的模式](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

