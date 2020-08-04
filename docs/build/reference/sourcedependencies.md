---
title: /sourceDependencies （報表來源層級相依性）
description: Microsoft c + + 中/sourceDependencies 編譯器選項的參考指南。
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 3198353ea7569c426a556522d6b931fe23c7f12c
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87528067"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies`（報表來源層級相依性）

指示編譯器產生 JSON 檔案，該檔案會詳細說明編譯期間所耗用的來源層級相依性。

JSON 檔案包含來源相依性的清單，其中包括：
- 標頭檔（可轉移和直接包含的標頭）。
- 使用的 PCH （如果 **`/Yu`** 有指定）。
- 匯入的模組和匯入的標頭單位（可轉移和直接匯入的模組/標頭單位）。

## <a name="syntax"></a>Syntax

> **`/sourceDependencies`***檔案名*\
> **`/sourceDependencies`***目錄*

## <a name="arguments"></a>引數

*名稱*\
編譯器會將來源相依性輸出寫入指定的檔案名，其中可能包含相對或絕對路徑。

*directory*\
如果引數是目錄，編譯器會在指定的目錄中產生來源相依性檔案。 輸出檔名稱是以輸入檔的完整名稱為基礎，加上附加的 *`.json`* 副檔名。 例如，如果提供給編譯器的檔案是 *`main.cpp`* ，則產生的輸出檔案名為 *`main.cpp.json`* 。

## <a name="remarks"></a>備註

**`/sourceDependencies`** 從 Visual Studio 2019 16.7 版開始，可以使用編譯器選項。 預設不會啟用此功能。

當您指定 **`/MP`** 編譯器選項時，建議您使用搭配 **`/sourceDependencies`** 目錄引數。 如果您提供單一 filename 引數，則兩個編譯器實例可能會嘗試同時開啟輸出檔案，並造成錯誤。 如需的詳細資訊 **`/MP`** ，請參閱[ `/MP` （使用多個進程建立）](mp-build-with-multiple-processes.md)。

當發生非嚴重的編譯器錯誤時，相依性資訊仍然會寫入至輸出檔案。

所有檔案路徑在輸出中會顯示為絕對路徑。

### <a name="examples"></a>範例

假設有下列範例程式碼：

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

您可以 **`/sourceDependencies`** 搭配使用編譯器選項的其餘部分：

> `cl ... /sourceDependencies output.json ... main.cpp`

其中 `...` 代表您的其他編譯器選項。 此命令列會產生 JSON 檔案 *`output.json`* ，其內容如下：

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

我們已使用 `...` 來將報告的路徑縮寫，此報表包含絕對路徑。 報告的路徑取決於編譯器尋找相依性的位置。 如果結果不是預期的，您可能會想要檢查項目的 include 路徑設定。

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/sourceDependencies 編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，新增 *`/sourceDependencies: <filename>`* ，然後選擇**Apply** **[確定]** 或 [套用] 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 此選項沒有程式設計的對等用法。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
