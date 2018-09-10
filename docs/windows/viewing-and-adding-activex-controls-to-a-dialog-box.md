---
title: 檢視及加入 ActiveX 控制項加入對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc5360a90690b27f1c52f97cd8b3746ddee5d60a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318378"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>檢視及加入 ActiveX 控制項加入對話方塊 （c + +）

Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。

### <a name="to-see-the-activex-controls-you-have-available"></a>查看您可使用的 ActiveX 控制項

1. 在 [對話方塊] 編輯器中開啟對話方塊。

2. 在對話方塊主體中的任意處按一下滑鼠右鍵。

3. 在捷徑功能表上，按一下 [插入 ActiveX 控制項] 。

   [[插入 ActiveX 控制項] 對話方塊](../windows/insert-activex-control-dialog-box.md) 會隨即出現，顯示您系統上所有的 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>在對話方塊中加入 ActiveX 控制項

1. 在 [[插入 ActiveX 控制項] 對話方塊](../windows/insert-activex-control-dialog-box.md)中，選取您要加入對話方塊中的控制項，然後按一下 [確定] 。

   該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。

   > [!NOTE]
   > 您可以將 ActiveX 控制項加入 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)。

   > [!CAUTION]
   > 在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱安裝這些控制項之軟體的授權合約，或連絡軟體公司。

   您可以放置在控制項**工具箱**視窗以方便存取。 如需詳細資訊，請參閱[工具箱](/visualstudio/ide/reference/toolbox)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)  
[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
[ActiveX 控制項容器](../mfc/activex-control-containers.md)