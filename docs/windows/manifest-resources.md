---
title: 資訊清單資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1520cd301fa46fb4d9521fd6d4180ebd3710f67
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218246"
---
# <a name="manifest-resources"></a>資訊清單資源

資訊清單資源是描述應用程式所用相依性的 XML 檔案。 例如，在 Visual Studio 中，MFC 精靈產生的資訊清單檔案會定義應用程式應該使用哪些 Windows 通用控制項 DLL (5.0 或 6.0 版)：

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

若要檢視版本和類型資訊清單資源內含的資訊，您可以開啟檔案的 XML 檢視器中，或在 Visual Studio[文字編輯器](https://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)。 如需詳細資訊，請參閱 [在 Visual Studio 文字編輯器中開啟資訊清單資源](../windows/how-to-open-a-manifest-resource.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： Using Resources for Localization with ASP.NET](https://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="limitations"></a>限制

每個模組只能有一個資訊清單資源。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)  
[使用資源檔](../windows/working-with-resource-files.md)