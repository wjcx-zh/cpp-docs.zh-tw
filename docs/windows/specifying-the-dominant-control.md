---
title: 指定主控 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog editor, dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93e8d1dff23d77d861a52d4f1531203ebd05987b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593292"
---
# <a name="specifying-the-dominant-control"></a>指定主控項

選取的控制項第一個是主要的控制項。

### <a name="to-specify-the-dominant-control"></a>若要指定主控項

1. 按住**Ctrl**鍵，然後按一下您想要的大小或其他控制項的位置會影響的控制項*第一個*。

   **請注意**主控項的調整大小控點是純色，而下層控制項的控制代碼是空心。 所有進一步調整大小或對齊根據主控制項。

### <a name="to-change-the-dominant-control"></a>若要變更主控項

1. 所有目前選取的控制項外按一下，以清除目前的選取範圍。

2. 重複上一個程序，第一次選取不同的控制項。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[選取多個控制項](../windows/selecting-multiple-controls.md)  
[選取控制項](../windows/selecting-controls.md)  
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)