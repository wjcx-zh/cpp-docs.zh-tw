---
title: 架構中的對話方塊元件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: b3290107337f60854e6abbd2f744aaa38af0b741
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616915"
---
# <a name="dialog-box-components-in-the-framework"></a>架構中的對話方塊元件

在 MFC 架構中，對話方塊具有兩個元件：

- 一個指定對話方塊的控制項及其位置的對話方塊範本資源。

   對話方塊資源會從 Windows 建立對話方塊視窗的地方儲存對話方塊範本，並顯示它。 範本可指定對話方塊的特性，包括它的大小、位置、樣式和對話方塊的控制項類型和位置。 您通常會使用儲存為資源的對話方塊範本，不過您也可以在記憶體中建立自己的範本。

- 衍生自[CDialog](reference/cdialog-class.md)的對話方塊類別，提供用來管理對話方塊的程式設計介面。

   對話方塊是一個視窗，會在可見時附加到 Windows 視窗。 當對話方塊視窗建立時，會使用對話方塊範本資源做為建立對話方塊子視窗控制項的範本。

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
