---
title: "Rich Edit 控制項中的段落格式化 |Microsoft 文件"
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
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f0dc12d923f6f424fe84768b0d934d8dd7ff20b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控制項中的段落格式化
您可以使用 rich edit 控制項的成員函式 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 來格式化段落和擷取格式化資訊。 段落格式屬性包含對齊、定位點、縮排和編號。  
  
 您可以套用段落格式使用[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成員函式。 若要判斷目前的段落格式選取的文字，請使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成員函式。 [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)結構用於搭配這些成員函式以指定段落屬性。 其中一個重要成員**PARAFORMAT**是**dwMask**。 在`SetParaFormat`， **dwMask**指定那些段落屬性會設定由這個函式呼叫。 `GetParaFormat`報告選取範圍; 中的第一個段落的屬性**dwMask**指定選取範圍中一致的屬性。  
  
## <a name="see-also"></a>請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

