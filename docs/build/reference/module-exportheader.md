---
title: '/module： exportHeader (建立標頭單位) '
description: 使用/module： exportHeader 編譯器選項來建立標頭名稱或包含所指定檔案的模組標頭單位。
ms.date: 09/13/2020
f1_keywords:
- /module:exportHeader
helpviewer_keywords:
- /module:exportHeader
- Create header units
ms.openlocfilehash: f0c0ce1c593df742af77aa36189df1e89de75b6b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079056"
---
# <a name="moduleexportheader-create-header-units"></a>`/module:exportHeader` (建立標頭單位) 

告知編譯器建立輸入引數所指定的標頭單位。 編譯器會在 IFC () 檔中產生輸出 *`.ifc`* 。

## <a name="syntax"></a>語法

> **`/module:exportHeader`** *`header-name`* \[...]\
> **`/module:exportHeader`** *`filename`* \[...]

### <a name="arguments"></a>引數

*`header-name`*\
要匯出的標頭檔。 *`header-name`* 引數必須採用與指示詞的引數相同的形式 `#include` 。

*`filename`*\
要從中建立標頭單位之標頭檔的相對或絕對路徑。

## <a name="remarks"></a>備註

**`/module:exportHeader`** 編譯器選項會要求您透過使用 [`/experimental:module`](experimental-module.md) 編譯器選項以及[/std： c + + 最新](std-specify-language-standard-version.md)選項來啟用實驗性模組支援。 從 Visual Studio 2019 16.8 版開始，可以使用此選項。

一個 **`/module:exportHeader`** 編譯器選項可指定您的組建所需的標頭名稱引數數目。 您不需要另外指定它們。

根據預設，編譯標頭單位時，編譯器不會產生物件檔。 若要產生物件檔案，請指定 **`/Fo`** 編譯器選項。 如需詳細資訊，請參閱[ `/Fo` (的目的檔名) ](fo-object-file-name.md)。

編譯器 *`header-name`* 會根據包含目錄搜尋順序（包括您指定的任何）來解析。 如需詳細資訊，請參閱[ `/I` (其他 include 目錄) ](i-additional-include-directories.md)。

引數的 *`header-name`* 指定方式必須與在來源中出現的方式相同。 引數對引號規則和 `<` 命令列上的和運算子而言很敏感 `>` 。 使用 VS2019 命令提示字元來建立標頭單位（例如使用命令提示字元）的正確命令可能如下所 `<vector>` 示：

```cmd
cl ... /experimental:module /module:exportHeader "<vector>"
```

建立本機專案標頭（例如） `"utils/util.h"` 可能看起來像這樣：

```cmd
cl ... /experimental:module /module:exportHeader """util/util.h"""
```

其他命令列處理器中的引號規則可能會不同。

使用的 *`header-name`* 表單時 **`/module:exportHeader`** ，您可能會發現使用互補選項很有説明 **`/module:showResolvedHeader`** 。 **`/module:showResolvedHeader`** 選項會列印引數所解析之檔案的絕對路徑 *`header-name`* 。

**`/module:exportHeader`** 可以一次處理多個輸入，甚至是在下 **`/MP`** 。 我們建議您使用 **`/module:output <directory>`** 來為每個編譯建立個別的 IFC 檔案。

### <a name="examples"></a>範例

在指定 `"C:\util\util.h"` 的標頭和 `"C:\app\app.h"` 中，您可以使用下列命令將它們匯出為 *`header-name`* 引數：

```cmd
cl /IC:\ /experimental:module /module:exportHeader """util/util.h""" """app/app.h""" /FoC:\obj
```

您可以使用下列命令，將它們匯出為 *`filename`* 引數：

```cmd
cl /IC:\ /experimental:module /module:exportHeader C:\util\util.h C:\app\app.h /FoC:\obj
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式清單設定為 [**所有**設定]。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性，以加入 *`/module:exportHeader`* 選項和任何引數。 然後，選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。

## <a name="see-also"></a>另請參閱

[`/experimental:module` (啟用模組支援) ](experimental-module.md)\
[`/headerUnit` (使用標頭單位 IFC) ](headerunit.md)\
[`/module:reference` (使用命名模組 IFC) ](module-reference.md)\
[`/translateInclude` (將 include 指示詞轉譯為匯入指示詞) ](translateinclude.md)
