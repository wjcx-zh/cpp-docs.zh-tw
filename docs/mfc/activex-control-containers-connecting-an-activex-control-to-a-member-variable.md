---
title: ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: c6bc063875f2a31c582c9de32e24e7dfbc7826c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394906"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數

從其控制項容器應用程式中存取 ActiveX 控制項的最簡單方式，是將 ActiveX 控制項與將包含控制項的對話方塊類別的成員變數相關聯。

> [!NOTE]
>  這不是從容器類別存取內嵌控制項的唯一方式，但是就本文的目的而言綽綽有餘。

### <a name="adding-a-member-variable-to-the-dialog-class"></a>將成員變數加入至對話方塊類別

1. 從類別檢視中，以滑鼠右鍵按一下主對話方塊類別，開啟捷徑功能表。 例如， `CContainerDlg` 。

1. 從快顯功能表中，按一下**新增**，然後**加入變數**。

1. 在 [加入成員變數精靈] 中，按一下**控制變數**。

1. 在 **控制項 ID**清單方塊中，選取內嵌 ActiveX 控制項的控制項 ID。 例如， `IDC_CIRCCTRL1` 。

1. 在 **變數的名稱**方塊中，輸入名稱。

   例如， *m_circctl*。

1. 按一下 **完成**接受您的選擇，並結束 加入成員變數精靈。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)
