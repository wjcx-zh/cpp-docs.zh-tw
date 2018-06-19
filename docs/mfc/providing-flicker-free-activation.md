---
title: 提供閃動 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9d9c0108ce4afd2e65678280248488181ad34f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356550"
---
# <a name="providing-flicker-free-activation"></a>提供避免重繪閃動
如果您的控制項繪製本身在非現用和現用狀態 （並不會使用無視窗啟用），您可以排除繪製作業以及非使用中之間的轉換時正常發生的視覺重繪和作用中狀態。 若要這樣做，請包含**noFlickerActivate**旗標所傳回的集合中的旗標[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如:   
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]  
  
 如果您選取，將自動產生納入這個旗標的程式碼**閃動**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面使用 [MFC ActiveX 控制項精靈] 建立控制項時。  
  
 如果您使用無視窗啟用，這個最佳化不會有作用。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

