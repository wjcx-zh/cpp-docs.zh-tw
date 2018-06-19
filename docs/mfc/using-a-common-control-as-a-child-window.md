---
title: 使用通用控制項做為子視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d21675d913211026a2077a0830b7d8ed1225c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382820"
---
# <a name="using-a-common-control-as-a-child-window"></a>將通用控制項做為子視窗使用
所有 Windows 通用控制項都可以做為其他視窗中的子視窗。 下列程序描述如何動態建立通用控制項並使用該控制項。  
  
### <a name="to-use-a-common-control-as-a-child-window"></a>使用通用控制項做為子視窗  
  
1.  在相關的類別或處理常式中定義控制項。  
  
2.  使用控制項的覆寫的[cwnd:: Create](../mfc/reference/cwnd-class.md#create)方法來建立 Windows 控制項。  
  
3.  在建立控制項後 (如果您子類別化控制項，則在 `OnCreate` 處理常式之前)，您可以使用其成員函式來操作控制項。 請參閱在個別控制項的描述[控制項](../mfc/controls-mfc.md)如需詳細資訊的方法。  
  
4.  當您使用控制項時，請使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)終結控制項。  
  
## <a name="see-also"></a>另請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)

