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
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371611"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數

從其控制項容器應用程式中存取 ActiveX 控制項的最簡單方式，是將 ActiveX 控制項與將包含控制項的對話方塊類別的成員變數相關聯。

> [!NOTE]
> 這不是從容器類別存取內嵌控制項的唯一方式，但是就本文的目的而言綽綽有餘。

### <a name="adding-a-member-variable-to-the-dialog-class"></a>將成員變數加入至對話方塊類別

1. 從類別檢視中，以滑鼠右鍵按一下主對話方塊類別，開啟捷徑功能表。 例如： `CContainerDlg` 。

1. 在快捷選單中,按下「**新增」 選「 新增」****選**量 。

1. 在「添加成員變數嚮導」中,按一下 **「控制變數**」。

1. 在 **「控制 ID」** 清單框中,選擇嵌入式 ActiveX 控制件的控制 ID。 例如： `IDC_CIRCCTRL1` 。

1. 在 **"變數名稱"** 框中,輸入名稱。

   例如 *,m_circctl*。

1. 按下 **「完成」** 以接受您的選擇並退出「新增成員變數精靈」。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)
