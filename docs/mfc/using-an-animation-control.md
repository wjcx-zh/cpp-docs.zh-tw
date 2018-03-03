---
title: "使用動畫控制項 |Microsoft 文件"
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
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38523c832f4a30f247bd3e1d0b8318f44f5c47b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-animation-control"></a>使用動畫控制項
動畫控制項的一般使用方式會遵循下列模式：  
  
-   建立控制項。 如果在對話方塊範本中指定控制項，就會隨對話方塊的建立而自動建立。 (您應該有[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)您對應至動畫控制項的對話方塊類別中的成員。)或者，您可以使用[建立](../mfc/reference/canimatectrl-class.md#create)做為任何視窗的子視窗建立控制項的成員函式。  
  
-   藉由呼叫載入動畫控制項的 AVI 短片[開啟](../mfc/reference/canimatectrl-class.md#open)成員函式。 如果動畫控制項位於對話方塊中，若要這樣做最好先在對話方塊類別[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式。  
  
-   藉由呼叫播放短片[播放](../mfc/reference/canimatectrl-class.md#play)成員函式。 如果動畫控制項位於對話方塊中，若要這樣做最好先在對話方塊類別**OnInitDialog**函式。 呼叫**播放**不需要動畫控制項有`ACS_AUTOPLAY`樣式設定。  
  
-   如果您想要顯示的剪輯部分或播放它框架，使用`Seek`成員函式。 若要停止播放剪輯，請使用`Stop`成員函式。  
  
-   如果您不會立即終結控制項時，從記憶體移除剪輯藉由呼叫**關閉**成員函式。  
  
-   如果動畫控制項位於對話方塊中，它和`CAnimateCtrl`物件將會自動終結。 否則，您必須確保控制項和 `CAnimateCtrl` 物件都已正確地終結。 終結控制項的自動關閉 AVI 短片。  
  
## <a name="see-also"></a>請參閱  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控制項](../mfc/controls-mfc.md)

