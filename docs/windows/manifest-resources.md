---
title: 資訊清單資源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850186"
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

對於 Windows XP 或 Windows Vista 應用程式，資訊清單資源不只會指定應用程式使用最新版的 Windows 通用控制項 (v6.0，如上所示)，也會支援 [Syslink 控制項](/windows/desktop/Controls/syslink-overview)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

若要檢視版本和類型資訊清單資源內含的資訊，您可以在 Visual Studio 文字編輯器或 XML 檢視器中開啟檔案。 如果您從 [ [資源檢視](../windows/resource-view-window.md)] 開啟資訊清單資源，資源會以二進位格式開啟。 若要檢視資訊清單資源的內容，以更利於檢視的格式，您必須開啟來自的資源**方案總管 中**。

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>在文字編輯器中開啟資訊清單資源

1. 與您的專案中開啟**方案總管**，展開**資源檔**資料夾。

1. 按兩下 .manifest 檔案。

   在中開啟您的資訊清單資源**文字編輯器**。

## <a name="to-open-a-manifest-resource-in-another-editor"></a>在另一個編輯器中開啟資訊清單資源

1. 在 **方案總管 中**，以滑鼠右鍵按一下.manifest 檔案，然後選擇 **開啟方式...** 從捷徑功能表。

1. 在 **開啟**對話方塊中，指定您想要使用，並選取編輯器**開啟**。

## <a name="limitations"></a>限制

每個模組只能有一個資訊清單資源。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)<br/>
[使用資源檔](../windows/working-with-resource-files.md)