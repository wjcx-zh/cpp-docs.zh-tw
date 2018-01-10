---
title: "ActiveX 控制項容器： 將 ActiveX 控制項連接至成員變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2248dd68b0ecc7471899552bcb7b0394f3f9f363
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數
從其控制項容器應用程式中存取 ActiveX 控制項的最簡單方式，是將 ActiveX 控制項與將包含控制項的對話方塊類別的成員變數相關聯。  
  
> [!NOTE]
>  這不是從容器類別存取內嵌控制項的唯一方式，但是就本文的目的而言綽綽有餘。  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>將成員變數加入至對話方塊類別  
  
1.  從類別檢視中，以滑鼠右鍵按一下主對話方塊類別，開啟捷徑功能表。 例如，`CContainerDlg`。  
  
2.  從捷徑功能表，按一下 **新增**然後**加入變數**。  
  
3.  在 加入成員變數精靈中，按一下 **控制變數**。  
  
4.  在**控制項 ID**清單方塊中，選取內嵌 ActiveX 控制項的控制項 ID。 例如，`IDC_CIRCCTRL1`。  
  
5.  在**變數名稱**方塊中，輸入名稱。  
  
     例如，`m_circctl`。  
  
6.  按一下**完成**接受您的選擇，並結束 加入成員變數精靈。  
  
## <a name="see-also"></a>請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)

