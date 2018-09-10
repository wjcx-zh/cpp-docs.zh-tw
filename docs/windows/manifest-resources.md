---
title: 資訊清單資源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d58e89250708f264ff6bb96c75e8124ffa02509
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316441"
---
# <a name="manifest-resources-c"></a>資訊清單資源 （c + +）

在 c + + 桌面專案中，資訊清單資源是描述應用程式使用的相依性的 XML 檔案。 例如，在 Visual Studio 中，MFC 精靈產生的資訊清單檔案會定義應用程式應該使用哪些 Windows 通用控制項 DLL (5.0 或 6.0 版)：

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Windows XP 或 Windows Vista 應用程式資訊清單資源不只會指定應用程式使用最新版本的 Windows 通用控制項 (v6.0，如上所示)，但它也支援[Syslink 控制項](/windows/desktop/Controls/syslink-overview)。

若要檢視版本和類型資訊清單資源內含的資訊，您可以在 Visual Studio 文字編輯器或 XML 檢視器中開啟檔案。 如需詳細資訊，請參閱 [在 Visual Studio 文字編輯器中開啟資訊清單資源](../windows/how-to-open-a-manifest-resource.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="limitations"></a>限制

每個模組只能有一個資訊清單資源。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)  
[使用資源檔](../windows/working-with-resource-files.md)