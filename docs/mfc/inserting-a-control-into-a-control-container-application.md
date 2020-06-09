---
title: ActiveX 控制項容器：將控制項插入控制項容器應用程式中
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 1d2fc82628b3bcf842a6efb1d36ab9e8389fc0ba
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618487"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控制項容器：將控制項插入控制項容器應用程式中

您必須先使用 [[插入 Activex 控制項](../windows/insert-activex-control-dialog-box.md)] 對話方塊，將 activex 控制項新增至容器應用程式，才能從 activex 控制項容器應用程式存取 activex 控制項。

若要將 ActiveX 控制項加入至 ActiveX 控制項容器專案，請參閱[在對話方塊中查看和加入 Activex 控制項](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

加入控制項之後，您必須將成員變數（屬於 ActiveX 控制項類型）新增至對話方塊類別。 如需此程式的詳細資訊，請參閱[新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)。

加入成員變數之後，就會自動產生類別（稱為包裝函式類別），並將其新增至您的專案。 這個類別是用來做為控制項容器和內嵌控制項之間的介面。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](activex-control-containers.md)
