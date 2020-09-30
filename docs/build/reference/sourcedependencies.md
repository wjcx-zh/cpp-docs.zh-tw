---
title: /sourceDependencies (報告來源層級相依性)
description: Microsoft c + + 中/sourceDependencies 編譯器選項的參考指南。
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 0c1866812435c777f6f1fd7ed7f9db788a8cf031
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502844"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies` (報表來源層級相依性) 

指示編譯器產生 JSON 檔案，以詳細說明編譯期間所使用的來源層級相依性。

JSON 檔案包含來源相依性的清單，包括：

- 標頭檔 () 的可轉移和直接包含的標頭。
- 如果) 指定，則使用 (的 PCH **`/Yu`** 。
- 匯入的模組和匯入的標頭單位 (可轉移和直接匯入的模組/標頭單位) 。

## <a name="syntax"></a>Syntax

> **`/sourceDependencies`***檔案名*\
> **`/sourceDependencies`***目錄*

## <a name="arguments"></a>引數

*檔案名*\
編譯器會將來源相依性輸出寫入指定的檔案名，其中可能包括相對或絕對路徑。

*目錄*\
如果引數是目錄，則編譯器會在指定的目錄中產生來源相依性檔案。 輸出檔名稱是根據輸入檔的完整名稱，加上附加的 *`.json`* 副檔名。 例如，如果提供給編譯器的檔案是 *`main.cpp`* ，則產生的輸出檔案名為 *`main.cpp.json`* 。

## <a name="remarks"></a>備註

**`/sourceDependencies`** 從 Visual Studio 2019 16.7 版開始，可以使用編譯器選項。 預設不會啟用。

當您指定 **`/MP`** 編譯器選項時，建議您使用 **`/sourceDependencies`** with directory 引數。 如果您提供單一檔案名引數，則編譯器的兩個實例可能會嘗試同時開啟輸出檔案，並導致錯誤。 如需的詳細資訊 **`/MP`** ，請參閱[ `/MP` (組建與多個進程) ](mp-build-with-multiple-processes.md)。

發生非嚴重的編譯器錯誤時，仍會將相依性資訊寫入輸出檔。

所有檔案路徑在輸出中會顯示為絕對路徑。

### <a name="examples"></a>範例

提供下列範例程式碼：

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

您可以 **`/sourceDependencies`** 搭配其餘的編譯器選項使用：

> `cl ... /sourceDependencies output.json ... main.cpp`

其中 `...` 代表您的其他編譯器選項。 此命令列會產生 *`output.json`* 具有類似下列內容的 JSON 檔案：

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

我們用 `...` 來縮寫報告的路徑，報表包含絕對路徑。 所報告的路徑取決於編譯器找到相依性的位置。 如果結果不是預期的，您可能會想要檢查項目的 [包含路徑] 設定。

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/sourceDependencies 編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，加入， *`/sourceDependencies: <filename>`* 然後選擇**Apply** **[確定]** 或 [套用] 以儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 此選項沒有程式設計對等專案。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
