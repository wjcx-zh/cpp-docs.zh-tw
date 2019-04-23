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
ms.openlocfilehash: 45db6d0139cfa3aa8a2eaa8fe6d18158cb6646ce
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029391"
---
# <a name="resource-files-c"></a>資源檔 (C++)

> [!NOTE]
> 。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從 **方案總管**。 使用[影像編輯器](../windows/image-editor-for-icons.md)並[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。
>
> 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

詞彙*資源檔*像可以參考多種檔案類型：

- 程式的資源指令碼 (.rc) 檔。

- 資源範本 (.rct) 檔。

- 存在為獨立檔案的個別資源。 此類型包含的.rc 檔案提及的點陣圖、 圖示或游標檔案。

- 標頭所產生的檔案在開發環境。 這種類型包括`Resource.h`，.rc 檔案提及。

例如.exe、.dll 和.res 檔稱為其他檔案類型 中找到的資源*資源*。

您可以使用*資源檔*並*資源*從您的專案內。 您也可以使用的不是目前專案的一部分，或在建立 Visual Studio 的開發環境以外的地方。 例如，您可以：

- 使用巢狀和條件限定的資源檔案。

- 更新現有的資源，或將它們轉換至視覺效果C++。

- 從目前的資源檔匯入或匯出圖形資源。

- 包含開發環境無法修改的共用或唯讀識別項 (符號)。

- 您不需要編輯 （或不應該編輯），例如數個專案之間共用資源的可執行檔 (.exe) 檔案中包含資源。

- 包含開發環境不支援的類型。

如需有關資源的詳細資訊，請參閱如何[建立的資源](../windows/how-to-create-a-resource-script-file.md)，[管理資源](../windows/how-to-copy-resources.md)，並[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

## <a name="editable-resources"></a>可編輯的資源

若要編輯所包含的資源，可以開啟下列類型的檔案：

| 檔案名稱 | 描述 |
|---|---|
| .rc | 資源指令碼檔案 |
| .rct | 資源範本檔 |
| .res | 資源檔 |
| .resx | Managed 的資源檔 |
| .exe | 可執行檔 |
| .dll | 動態連結程式庫檔案 |
| .bmp, .ico, .dib, .cur | 點陣圖、 圖示、 工具列和游標檔案 |

當編輯資源，Visual Studio 環境與搭配運作，而且會影響下列檔案：

| 檔案名稱 | 描述 |
|---|---|
| 偵錯工具 | 包含符號定義的開發環境所產生的標頭檔。<br/><br/>原始檔控制中包含此檔案。 |
| Filename.aps | 用於快速載入的目前資源指令碼檔的二進位版本。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成.aps 檔所使用的資源編輯器。 此檔案是一個編譯步驟，只會儲存符號資料。<br/><br/>正常編譯處理程序，在編譯程序期間會捨棄未符號，例如註解的資訊。<br/><br/>每當.aps 檔未與.rc 檔同步處理時，會重新產生.rc 檔。 例如，當您**儲存**，資源編輯器會覆寫.rc 檔和 resource.h 檔案。 資源本身的任何變更繼續合併在.rc 檔，但總是遺失註解，一旦.rc 檔被覆寫。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。<br/><br/>一般而言，您不應包含.aps 檔未在原始檔控制。 |
| .rc | 包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。<br/><br/>原始檔控制中包含此檔案。 |

## <a name="manifest-resources"></a>資訊清單資源

在C++傳統型專案中，資訊清單資源是描述應用程式使用的相依性的 XML 檔案。 例如，在 Visual Studio 這個 MFC 精靈產生資訊清單檔案定義應用程式應該使用哪個版本的 Windows 通用控制項 Dll:

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

Windows XP 或 Windows Vista 應用程式資訊清單資源應該指定應用程式使用的 Windows 通用控制項的最新版本。 上述範例中使用版本`6.0.0.0`，支援[Syslink 控制項](/windows/desktop/Controls/syslink-overview)。

> [!NOTE]
> 每個模組只能有一個資訊清單資源。

若要檢視版本和類型資訊清單資源內含的資訊，請在 XML 檢視器] 或 [Visual Studio 文字編輯器中開啟檔案。 如果您從 [ [資源檢視](../windows/resource-view-window.md)] 開啟資訊清單資源，資源會以二進位格式開啟。

### <a name="to-open-a-manifest-resource"></a>若要開啟 資訊清單資源

1. 在 Visual Studio 中開啟您的專案，並瀏覽至**方案總管 中**。

1. 依序展開**資源檔**資料夾，然後：

   - 若要在文字編輯器中開啟，按兩下 *.manifest*檔案。

   - 若要開啟在其他編輯器中，以滑鼠右鍵按一下 *.manifest*檔案，然後選取**開啟**。 指定編輯器使用，並選取**開啟**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>