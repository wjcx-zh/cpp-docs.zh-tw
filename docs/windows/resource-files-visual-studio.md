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
ms.openlocfilehash: b66a207766962856cc4d7181607868c2a48ebe84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513653"
---
# <a name="resource-files-c"></a>資源檔 (C++)

> [!NOTE]
> 。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從 **方案總管**。 使用[影像編輯器](../windows/image-editor-for-icons.md)和[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。
>
> 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

「*資源檔*」一詞可以參考數種檔案類型, 例如:

- 程式的資源指令碼 (.rc) 檔。

- 資源範本 (.rct) 檔。

- 以獨立檔案形式存在的個別資源。 此類型包含從 .rc 檔參考的點陣圖、圖示或游標檔案。

- 開發環境所產生的標頭檔。 這種類型`Resource.h`包括, 這是從 .rc 檔參考的。

在其他檔案類型 (例如 .exe、.dll 和 .res 檔案) 中找到的資源稱為「*資源*」。

您可以從專案內使用*資源檔*和*資源*。 您也可以使用不屬於目前專案的元件, 或在 Visual Studio 的開發環境之外建立。 例如，您可以：

- 使用巢狀和條件限定的資源檔案。

- 更新現有的資源, 或將它們C++轉換成視覺效果。

- 從目前的資源檔匯入或匯出圖形資源。

- 包含開發環境無法修改的共用或唯讀識別項 (符號)。

- 包含您的可執行檔 (.exe) 中不需要編輯 (或不應編輯) 的資源, 例如數個專案之間的共用資源。

- 包含開發環境不支援的類型。

如需資源的詳細資訊, 請參閱如何[建立資源](../windows/how-to-create-a-resource-script-file.md)、[管理資源](../windows/how-to-copy-resources.md), 以及[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

## <a name="editable-resources"></a>可編輯的資源

您可以開啟下列類型的檔案來編輯其包含的資源:

| 檔案名稱 | 說明 |
|---|---|
| .rc | 資源腳本檔 |
| .rct | 資源範本檔案 |
| .res | 資源檔 |
| .resx | 受控資源檔 |
| .exe | 可執行檔 |
| .dll | 動態連結程式庫檔案 |
| .bmp、.ico、.dib、中 | 點陣圖、圖示、工具列和游標檔案 |

編輯資源時, Visual Studio 環境會與搭配使用, 並影響下列檔案:

| 檔案名稱 | 說明 |
|---|---|
| 偵錯工具 | 包含符號定義的開發環境所產生的標頭檔。<br/><br/>將此檔案包含在原始檔控制中。 |
| Filename.aps | 用於快速載入之目前資源腳本檔案的二進位版本。<br /><br /> 資源編輯器不會直接讀取 .rc 或資源 .h 檔案。 資源編譯器會將它們編譯為資源編輯器所使用的 ap 檔案。 此檔案是一個編譯步驟，只會儲存符號資料。<br/><br/>就像一般的編譯器一樣, 在編譯過程中會捨棄不是符號的資訊, 例如批註。<br/><br/>當 ap 檔案與 .rc 檔案不同步時, 會重新產生 .rc 檔案。 例如, 當您**儲存**時, 資源編輯器會覆寫 .rc 檔和資源 .h 檔案。 資源本身的任何變更都會保留在 .rc 檔中, 但是一旦覆寫 .rc 檔案, 批註一定會遺失。 如需如何保留批註的相關資訊, 請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。<br/><br/>一般來說, 您不應該在原始檔控制中包含此 ap 檔案。 |
| .rc | 包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。<br/><br/>將此檔案包含在原始檔控制中。 |

## <a name="manifest-resources"></a>資訊清單資源

在C++桌面專案中, 資訊清單資源是描述應用程式所使用之相依性的 XML 檔案。 例如, 在 Visual Studio 此 MFC wizard 產生的資訊清單檔案會定義應用程式應使用的 Windows 通用控制項 Dll 版本:

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

對於 Windows XP 或 Windows Vista 應用程式, 資訊清單資源應指定最新版本的 Windows 通用控制項, 以供應用程式使用。 上述範例會使用支援`6.0.0.0` [Syslink 控制項](/windows/win32/Controls/syslink-overview)的版本。

> [!NOTE]
> 每個模組只能有一個資訊清單資源。

若要查看資訊清單資源中包含的版本和類型資訊, 請在 XML 檢視器或 Visual Studio 文字編輯器中開啟檔案。 如果您從 [ [資源檢視](../windows/resource-view-window.md)] 開啟資訊清單資源，資源會以二進位格式開啟。

### <a name="to-open-a-manifest-resource"></a>開啟資訊清單資源

1. 在 Visual Studio 中開啟您的專案, 然後流覽至 [**方案總管**]。

1. 展開 [**資源檔**] 資料夾, 然後:

   - 若要在文字編輯器中開啟, 請按兩下 *.manifest*檔案。

   - 若要在其他編輯器中開啟, 請以滑鼠右鍵按一下 *.manifest*檔案, 然後選取 [**開啟方式**]。 指定要使用的編輯器, 然後選取 [**開啟**]。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>