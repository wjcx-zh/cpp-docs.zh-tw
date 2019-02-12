---
title: 資源檔 (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 65500644b70841f372edcc6911edefc6c7b9f432
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152686"
---
# <a name="resource-files-c"></a>資源檔 (C++)

> [!NOTE]
> 這份資料適用於 Windows 桌面應用程式。 通用 Windows 平台應用程式中資源的詳細資訊，請參閱[定義應用程式資源](/windows/uwp/app-resources/)。
>
> 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。
>
> 。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從 **方案總管**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

「資源檔案」一詞表示多種檔案類型，包括：

- 程式的資源指令碼 (.rc) 檔。

- 資源範本 (.rct) 檔。

- 以獨立檔案形態存在的個別資源，例如 .rc 檔案提及的點陣圖、圖示或游標檔。

- 開發環境產生的標頭檔，例如 .rc 檔案提及的 Resource.h。

資源也位於[其他檔案類型](../windows/editable-file-types-for-resources.md)例如.exe、.dll 和.res 檔案。 您可以使用資源和資源檔案中您的專案，而不是目前專案的一部分。 您也可以使用 Visual Studio 的開發環境中建立的資源檔。 例如，您可以：

- 使用巢狀和條件限定的資源檔案。

- 更新現有的資源，或將它們轉換成 Visual C++ 格式。

- 從目前的資源檔匯入或匯出圖形資源。

- 包含開發環境無法修改的共用或唯讀識別項 (符號)。

- 包含可執行檔 (.exe) 檔案在您目前的專案，例如數個專案之間共用資源時，它們不需要編輯 （或不應該編輯） 中的資源。

- 包含開發環境不支援的類型。

您可以開啟下列檔案類型，然後編輯所包含的資源：

|檔案名稱|描述|
|---------------|-----------------|
|.rc|資源指令碼檔。|
|.rct|資源範本檔。|
|.res|資源檔。|
|.resx|Managed 資源檔。|
|.exe|可執行檔。|
|.dll|動態連結程式庫檔案。|
|.bmp、.ico、.dib 和 .cur|點陣圖、圖示、工具列和游標檔案。|

適用於 Visual Studio 環境，並會影響您資源的編輯工作階段期間顯示在下表中的檔案：

|檔案名稱|描述|
|---------------|-----------------|
|偵錯工具|開發環境所產生的標頭檔；包含符號定義。 （原始檔控制中包含此檔案）。|
|Filename.aps|目前資源指令碼檔的二進位版本；用於快速載入。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 正常編譯處理程序，在編譯程序期間會捨棄未符號 （例如，註解） 的資訊。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。 （一般而言，您不應該包含.aps 檔未在原始檔控制中）。|
|.rc|包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。 （原始檔控制中包含此檔案）。|

本節說明如何：

- [建立資源](../windows/how-to-create-a-resource-script-file.md)

- [管理資源](../windows/how-to-copy-resources.md)

- [在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)

## <a name="manifest-resources"></a>資訊清單資源

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

Windows XP 或 Windows Vista 應用程式資訊清單資源不只會指定應用程式會使用 Windows 通用控制項，v6.0，最新版本，如上所示，但它也支援[Syslink 控制項](/windows/desktop/Controls/syslink-overview)。

若要檢視版本和類型資訊清單資源內含的資訊，您可以在 Visual Studio 文字編輯器或 XML 檢視器中開啟檔案。 如果您從 [ [資源檢視](../windows/resource-view-window.md)] 開啟資訊清單資源，資源會以二進位格式開啟。 若要檢視資訊清單資源的內容，以更利於檢視的格式，您必須開啟來自的資源**方案總管 中**。

若要開啟資訊清單資源，選擇 從下列步驟：

- 文字編輯器，與您的專案中開啟**方案總管**，展開**資源檔**資料夾，然後按兩下.manifest 檔案。

- 另一個編輯器，在**方案總管] 中**，以滑鼠右鍵按一下.manifest 檔案，然後選擇 [**開啟方式...** 從捷徑功能表。 在 **開啟**對話方塊中，指定您想要使用，並選取編輯器**開啟**。

> [!NOTE]
> 每個模組只能有一個資訊清單資源。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[使用資源檔](../windows/working-with-resource-files.md)<br/>
[功能表與其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[控制項](../mfc/controls-mfc.md)<br/>