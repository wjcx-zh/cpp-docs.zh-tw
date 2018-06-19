---
title: 架構中的對話方塊元件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a92846dc1d7b950d1eccfa4cd42b01ac84d96b34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343963"
---
# <a name="dialog-box-components-in-the-framework"></a>架構中的對話方塊元件
在 MFC 架構中，對話方塊具有兩個元件：  
  
-   一個指定對話方塊的控制項及其位置的對話方塊範本資源。  
  
     對話方塊資源會從 Windows 建立對話方塊視窗的地方儲存對話方塊範本，並顯示它。 範本可指定對話方塊的特性，包括它的大小、位置、樣式和對話方塊的控制項類型和位置。 您通常會使用儲存為資源的對話方塊範本，不過您也可以在記憶體中建立自己的範本。  
  
-   對話方塊類別，衍生自[CDialog](../mfc/reference/cdialog-class.md)，以便為管理對話方塊中提供的程式設計介面。  
  
     對話方塊是一個視窗，會在可見時附加到 Windows 視窗。 當對話方塊視窗建立時，會使用對話方塊範本資源做為建立對話方塊子視窗控制項的範本。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

