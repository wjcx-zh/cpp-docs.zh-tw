---
title: 如何： 開啟資訊清單資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], opening
ms.assetid: bd6f9c47-2a1e-417d-9d2a-c1ad7d3b9635
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 53b414507fe2d21f610be1cd6a4db3bfce9628d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42550657"
---
# <a name="how-to-open-a-manifest-resource"></a>如何：開啟資訊清單資源

如果您從 [ [資源檢視](../windows/resource-view-window.md)] 開啟資訊清單資源，資源會以二進位格式開啟。 若要檢視資訊清單資源的內容，以更利於檢視的格式，您必須開啟來自的資源**方案總管 中**。

### <a name="to-open-a-manifest-resource-in-the-text-editor"></a>在文字編輯器中開啟資訊清單資源

1. 與您的專案中開啟**方案總管**，展開**資源檔**資料夾。

2. 按兩下 .manifest 檔案。

   在中開啟您的資訊清單資源**文字編輯器**。

### <a name="to-open-a-manifest-resource-in-another-editor"></a>在另一個編輯器中開啟資訊清單資源

1. 在 **方案總管 中**，以滑鼠右鍵按一下.manifest 檔案，然後選擇 **開啟方式...** 從捷徑功能表。

2. 在 [ **開啟方式** ] 對話方塊中，指定您要使用編輯器，然後按一下 [ **開啟**]。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資訊清單資源](../windows/manifest-resources.md)  
[控制項](../mfc/controls-mfc.md)  
[使用資源檔](../windows/working-with-resource-files.md)