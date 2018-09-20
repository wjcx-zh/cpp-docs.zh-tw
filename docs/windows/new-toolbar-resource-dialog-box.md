---
title: 新增工具列資源對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc933905cf4056d2be6c692728c621913687a6fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425531"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>新增工具列資源對話方塊 （c + +）

**新增工具列資源**對話方塊可讓您指定您要加入至 c + + 專案中工具列資源按鈕的高度與寬度。 預設值是 16 × 15 像素。

用來建立工具列點陣圖具有最大寬度為 2048年。 因此，如果您設定** 按鈕寬度**設為 512，您只能有四個按鈕。 如果您將寬度設成 513，您只能有三個按鈕。

### <a name="button-width"></a>按鈕寬度

提供空間讓您輸入會從一個點陣圖資源轉換成工具列資源的工具列按鈕的寬度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。

### <a name="button-height"></a>按鈕高度

提供空間讓您輸入會從一個點陣圖資源轉換成工具列資源的工具列按鈕的高度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[工具列按鈕屬性](../windows/toolbar-button-properties.md)<br/>
[轉換點陣圖為工具列](../windows/converting-bitmaps-to-toolbars.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)