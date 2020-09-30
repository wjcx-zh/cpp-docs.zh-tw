---
title: ActiveX 控制項容器：將控制項插入控制項容器應用程式中
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: e8426fd7a420ef06650930e547d06c78cc094975
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503107"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控制項容器：將控制項插入控制項容器應用程式中

您必須先使用 [ [插入 Activex 控制項](../windows/adding-editing-or-deleting-controls.md) ] 對話方塊，將 activex 控制項新增至容器應用程式，才能從 activex 控制項容器應用程式存取 activex 控制項。

若要將 ActiveX 控制項加入至 ActiveX 控制項容器專案，請參閱 [在對話方塊中查看和新增 Activex 控制項](../windows/adding-editing-or-deleting-controls.md)。

加入控制項之後，您必須將 ActiveX 控制項類型的成員變數 (新增) 至對話方塊類別。 如需此程式的詳細資訊，請參閱 [新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)。

一旦您加入成員變數，就會自動產生一個稱為包裝函式類別的類別，並將其新增至您的專案。 這個類別是用來做為控制項容器與內嵌控制項之間的介面。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](activex-control-containers.md)
