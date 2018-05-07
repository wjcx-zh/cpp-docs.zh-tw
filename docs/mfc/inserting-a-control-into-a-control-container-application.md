---
title: ActiveX 控制項容器： 將控制項插入控制項容器應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 716c045fc10b4dd5f3dede20a233d958e669bbd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控制項容器：將控制項插入控制項容器應用程式中
您可以從 ActiveX 控制項容器應用程式存取 ActiveX 控制項之前，您必須加入 ActiveX 控制項容器應用程式使用[插入 ActiveX 控制項](../windows/insert-activex-control-dialog-box.md) 對話方塊。  
  
 若要將 ActiveX 控制項加入至 ActiveX 控制項容器專案，請參閱[檢視及加入 ActiveX 控制項加入至對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 一旦您加入的控制項，您需要將類型成員變數 （ActiveX 控制項） 加入至對話方塊類別。 如需有關這個程序的詳細資訊，請參閱[加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)。  
  
 一旦您已加入成員變數的類別，稱為包裝函式類別是自動產生並加入至專案。 這個類別用做為控制項容器和內嵌的控制項之間的介面。  
  
## <a name="see-also"></a>另請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)

