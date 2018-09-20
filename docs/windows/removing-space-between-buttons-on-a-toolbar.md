---
title: 移除 （c + +） 工具列按鈕之間的空間 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
ms.assetid: 3bbbacec-cd42-4c35-9ea5-de62daa4041d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a925ad172e5cf146d830207383d4bad0da57ff9e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417564"
---
# <a name="removing-space-between-buttons-on-a-toolbar-c"></a>移除 （c + +） 工具列按鈕之間的空間

下列程序會示範如何移除工具列按鈕之間的空格。

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>若要移除工具列按鈕之間的空格

1. 拖曳按鈕空間的另一端的按鈕朝著空間的某一邊，直到它重疊偶數的相關的下一步 按鈕。

   如果沒有側邊的按鈕，您正在拖曳離開的空間，而且您將按鈕拖曳多個中間時，[相鄰] 按鈕，過去**工具列**編輯器也會插入您的按鈕的空間相對的一邊拖曳。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[建立、移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)