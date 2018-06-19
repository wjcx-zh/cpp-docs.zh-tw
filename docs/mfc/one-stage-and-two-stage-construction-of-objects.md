---
title: 一階段和兩階段的物件建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c53f99932887acad4d2eab5c15ed73b66b359fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346008"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>一階段和兩階段的物件建構
您可以建立圖形物件，例如畫筆和筆刷的兩個技術之間選擇：  
  
-   *一階建構*： 建構並初始化物件，在一個階段中，所有的建構函式。  
  
-   *兩階段建構*： 建構並初始化物件的兩個不同的階段。 建構函式建立物件，並初始化函式將它初始化。  
  
 兩階段建構永遠是安全的。 一階段建構中建構函式無法擲回例外狀況，如果您提供正確的引數或記憶體配置失敗。 雖然您還是必須檢查有錯誤的兩階段建構時，避免這個問題。 在任一情況下，終結該物件是相同的程序。  
  
> [!NOTE]
>  這些技術，亦適用於建立任何物件，不只圖形物件。  
  
## <a name="example-of-both-construction-techniques"></a>這兩種建構技巧的範例  
 下列簡單範例顯示建構畫筆物件的兩種方法：  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
-   [選取圖形物件放入裝置內容](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [裝置內容](../mfc/device-contexts.md)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>另請參閱  
 [圖形物件](../mfc/graphic-objects.md)

