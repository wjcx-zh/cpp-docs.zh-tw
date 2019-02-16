---
title: 資源檔 (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 4d56a62dfa350b3113a28355433130563464c6be
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320532"
---
# <a name="resource-files-c"></a>資源檔 (C++)

> [!NOTE]
> 。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從 **方案總管**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

「資源檔案」一詞表示多種檔案類型，包括：

- 程式的資源指令碼 (.rc) 檔。

- 資源範本 (.rct) 檔。

- 以獨立檔案形態存在的個別資源，例如 .rc 檔案提及的點陣圖、圖示或游標檔。

- 開發環境產生的標頭檔，例如 .rc 檔案提及的 Resource.h。

資源也可位於其他檔案類型，例如.exe、.dll 和.res 檔。 您可以使用資源和資源檔案中您的專案，而不是目前專案的一部分。 您也可以使用 Visual Studio 的開發環境中建立的資源檔。 例如，您可以：

- 使用巢狀和條件限定的資源檔案。

- 更新現有的資源，或將它們轉換成 Visual C++ 格式。

- 從目前的資源檔匯入或匯出圖形資源。

- 包含開發環境無法修改的共用或唯讀識別項 (符號)。

- 包含可執行檔 (.exe) 檔案在您目前的專案，例如數個專案之間共用資源時，它們不需要編輯 （或不應該編輯） 中的資源。

- 包含開發環境不支援的類型。

本節說明如何：

- [建立資源](../windows/how-to-create-a-resource-script-file.md)

- [管理資源](../windows/how-to-copy-resources.md)

- [在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)

## <a name="editable-resource-file-types"></a>可編輯的資源檔類型

若要編輯所包含的資源，可以開啟下列類型的檔案：

|檔案名稱|描述|
|---------|-----------------|
|.rc|資源指令碼檔案|
|.rct|資源範本檔|
|.res|資源檔|
|.resx|Managed 的資源檔|
|.exe|可執行檔|
|.dll|動態連結程式庫檔案|
|.bmp、.ico、.dib 和 .cur|點陣圖、圖示、工具列和游標檔案。|

Visual Studio 環境與搭配運作，並在您的資源編輯工作階段期間會影響下列檔案：

|檔案名稱|描述|
|---------------|-----------------|
|偵錯工具|開發環境所產生的標頭檔；包含符號定義。 （原始檔控制中包含此檔案）。|
|Filename.aps|目前資源指令碼檔的二進位版本；用於快速載入。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 正常編譯處理程序，在編譯程序期間會捨棄未符號 （例如，註解） 的資訊。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。 （一般而言，您不應該包含.aps 檔未在原始檔控制中）。|
|.rc|包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。 （原始檔控制中包含此檔案）。|

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

### <a name="to-open-a-manifest-resource"></a>若要開啟 資訊清單資源

1. 在 Visual Studio 中開啟專案。

1. 瀏覽至**方案總管**並展開**資源檔**資料夾。

   - 文字編輯器 中，按兩下.manifest 檔案。

   - 其他編輯器中，以滑鼠右鍵按一下.manifest 檔案，然後選取**開啟方式...**，然後指定編輯器使用，並選擇**開啟**。

> [!NOTE]
> 每個模組只能有一個資訊清單資源。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源識別項 （符號）](../windows/symbols-resource-identifiers.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>