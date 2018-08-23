---
title: 調整個別控制項的大小 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 929cf8eea66b928fe4889a98ca0a78fa7224bf17
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612504"
---
# <a name="sizing-individual-controls"></a>調整個別控制項的大小

您可以使用調整大小控點來調整控制項大小。 當指標位於其上的縮放控點時，它會變更形狀，以表示控制項可以在其中調整大小的指示。 作用中的縮放控點是純色;如果空心的縮放控點，則無法調整大小控制該軸。

您也可以藉由貼齊輔助線或邊界，以控制變更控制項大小或移動其中一個貼齊控制項和輔助線與另一個。

### <a name="to-size-a-control"></a>若要調整控制項的大小

1. 選取的控制項。

2. 拖曳調整大小控點，若要變更控制項的大小：

   - 在頂端和側邊的調整大小控點會變更水平或垂直大小。

   - 邊角調整大小控點會變更水平和垂直大小。

   > [!TIP]
   > 一次調整控制項的一個對話方塊單位 (DLU) 大小按住**Shift**鍵並使用**向右箭號**並**向下箭號**索引鍵。

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自動調整大小以容納內文字的控制項

1. 選擇**內容的大小**從**格式**功能表。

\-或-

- 以滑鼠右鍵按一下控制項，然後選擇 **內容的大小**從捷徑功能表。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)  
[控制項](../mfc/controls-mfc.md)