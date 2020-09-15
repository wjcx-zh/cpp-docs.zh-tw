---
title: '/translateInclude (將 include 指示詞轉譯為匯入指示詞) '
description: '使用/translateInclude 編譯器選項，將可匯入標頭名稱的 #include 指示詞轉譯為 import 標頭名稱指示詞。'
ms.date: 09/13/2020
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: 0050f2cb117e48d69cf97a587ef128b9b45790af
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079055"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (將 include 指示詞轉譯為匯入指示詞) 

告知編譯器將可匯入標頭名稱的指示詞轉譯為指示詞 `#include` `import header-name;` ，而不是使用文字包含。

## <a name="syntax"></a>語法

> **`/translateInclude`**

## <a name="remarks"></a>備註

**`/translateInclude`** 編譯器選項會要求您透過使用 [`/experimental:module`](experimental-module.md) 編譯器選項以及[/std： c + + 最新](std-specify-language-standard-version.md)選項來啟用實驗性模組支援。 從 Visual Studio 2019 16.8 版開始，可以使用此選項。

**`/translateInclude`** 選項可有效進行下列轉換，其中範例 `<vector>` 是可匯入的標頭單位：

```cpp
#include <vector>
```

編譯器會將這個指示詞取代為：

```cpp
import <vector> ;
```

在 MSVC 中，可匯入的標頭單位是以參考命名的單元 **`/headerUnit`** 。 如需詳細資訊，請參閱[ `/headerUnit` (使用頁首單位 IFC) ](headerunit.md)。

### <a name="examples"></a>範例

假設有一個專案參考兩個標頭檔和其標頭單位，如下表所列：

| 標頭檔 | IFC 檔案 |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

以及 *`.cpp`* 包含標頭的原始程式檔。

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

**`/translateInclude`** 選項可讓編譯器匯入標頭單位，而不是再次編譯標頭。 以下是範例命令列，它會將和的 include 指示詞轉譯 *`util.h`* *`app.h`* 成匯入標頭單位的匯入：

```CMD
cl /IC:\ /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式清單設定為 [**所有**設定]。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性以新增 *`/translateInclude`* 選項。 然後，選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。

## <a name="see-also"></a>另請參閱

[`/experimental:module` (啟用模組支援) ](experimental-module.md)\
[ `/headerUnit` (使用標頭單位 IFC) ](headerunit.md)。 \
[`/module:exportHeader` (建立標頭單位) ](module-exportheader.md)\
[`/module:reference` (使用命名模組 IFC) ](module-reference.md)
