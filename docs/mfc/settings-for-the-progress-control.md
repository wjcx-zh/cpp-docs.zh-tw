---
title: 進度控制項的設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26afdcb58a64f2d2042596349acc4496aa530468
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380005"
---
# <a name="settings-for-the-progress-control"></a>進度控制項的設定
進度控制項的基本設定 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) 的範圍和目前的位置。 範圍代表整個作業的持續時間。 目前的位置表示您的應用程式已完成此作業的進度。 範圍或位置的任何變更會導致重繪其本身的進度控制項。  
  
 根據預設，範圍設定為 0-100，而初始位置設定為 0。 若要擷取目前的範圍設定進度控制項，請使用[GetRange](../mfc/reference/cprogressctrl-class.md#getrange)成員函式。 若要變更的範圍，請使用[SetRange](../mfc/reference/cprogressctrl-class.md#setrange)成員函式。  
  
 若要設定的位置，使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)。 若要擷取目前的位置，而不指定新的值，使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。 例如，您可以直接查詢目前作業的狀態。  
  
 若要逐步進行控制項的目前位置，使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)。 若要設定的每個步驟，使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>另請參閱  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控制項](../mfc/controls-mfc.md)

