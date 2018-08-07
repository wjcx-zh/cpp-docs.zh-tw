---
title: 選取控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, selecting controls
- dominant controls
- dialog box controls, selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c8a7a57b263fc3db1fa7f021c1a6f4e09c0f8f7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605665"
---
# <a name="selecting-controls"></a>選取控制項
選取控制項來調整大小、 對齊、 移動、 複製或刪除它們，然後再執行您要的作業。 在大部分情況下，您必須選取要使用的調整大小和對齊工具上的多個控制項[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。  
  
 當控制項被選取時，它具有實線 (active）) 其周圍的灰色的框線或中空 （非作用中） 「 調整大小控點，「 小方塊，會出現在選取範圍框線。 主控多個控制項選取時，有穩固的調整大小控點;所有其他選取的控制項有空心的調整大小控點。  
  
 當您調整大小，或對齊多個控制項時，對話方塊編輯器使用的 「 主控制項 」 來判斷如何調整大小或對齊其他控制項。 根據預設，主控制項是第一個選取的控制項。  
  
-   [選取多個控制項](../windows/selecting-multiple-controls.md)  
  
-   [指定主控項](../windows/specifying-the-dominant-control.md)  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)