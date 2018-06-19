---
title: CStatusBarCtrl 的設定 |Microsoft 文件
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
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eea701c33001ffa3585c2d5847f3056454b7850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380158"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的設定
預設位置[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)狀態視窗底端的父視窗，但您可以指定`CCS_TOP`讓它出現在父視窗工作區頂端的樣式。  
  
 您可以指定**SBARS_SIZEGRIP**包括最右邊的調整大小底框樣式`CStatusBarCtrl`狀態視窗。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。  
  
> [!NOTE]
>  如果您合併`CCS_TOP`和**SBARS_SIZEGRIP**樣式，產生的調整大小底框不是功能即使系統則會在狀態視窗中繪製它。  
  
 狀態視窗的視窗程序會自動設定控制項視窗的初始大小和位置。 這個寬度與父視窗工作區的寬度相同。 高度根據目前選取到狀態視窗的裝置內容的字型度量資訊和視窗框線寬度。  
  
 視窗程序會在收到 `WM_SIZE` 訊息時自動調整狀態視窗的大小。 通常，當父視窗大小變更時，父視窗會傳送 `WM_SIZE` 訊息到狀態視窗。  
  
 您可以藉由呼叫設定狀態視窗的繪圖區域的最小高度[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)，指定最小高度，單位為像素。 繪圖區域不包括視窗框線。  
  
 您藉由呼叫擷取狀態視窗的框線寬度[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)。 此成員函式包含三元素陣列的指標，會接收水平框線、垂直框線和矩形間框線的寬度。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

