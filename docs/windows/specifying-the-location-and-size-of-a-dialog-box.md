---
title: 指定的位置和大小的對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 854e4df84bfc5f75eda8f98fa117c199ba054b3a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316571"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>指定的位置和大小的對話方塊 （c + +）

位置和大小的 c + + 對話方塊中，並將位置和大小的控制項，會以對話方塊單位。 個別控制項和對話方塊中的值會出現在右下角的 Visual Studio 狀態列上選取它們。

有三個屬性，您可以在設定[屬性 視窗](/visualstudio/ide/reference/properties-window)指定對話方塊會出現在螢幕上。 **Center**屬性是布林值; 如果您將值設定為 **，則為 True**，對話方塊一律會出現在螢幕的中央。 如果您將它設定為**False**，然後您可以設定**XPos**並**YPos**屬性，以明確地定義在螢幕上會出現的對話方塊。 [位置] 屬性會從左上角的 [檢視] 區域中，因為其定義如下的位移的值`{X=0, Y=0}`。 位置也根據**Absolute Align**屬性： 如果 **，則為 True**，座標是相對於畫面; 如果**False**，座標是相對於對話方塊擁有者的視窗。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)  
[控制項](../mfc/controls-mfc.md)