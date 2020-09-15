---
title: '/module：參考 (使用命名模組 IFC) '
description: 使用/module： reference 編譯器選項來建立標頭名稱或包含所指定檔案的模組標頭單位。
ms.date: 09/13/2020
f1_keywords:
- /module:reference
helpviewer_keywords:
- /module:reference
- Use named module IFC
ms.openlocfilehash: 5f40f6b700c38f3238cc7a621313621085fbc289
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079067"
---
# <a name="modulereference-use-named-module-ifc"></a>`/module:reference` (使用命名模組 IFC) 

告知編譯器使用現有的 IFC (*`.ifc`*) 進行目前的編譯。

## <a name="syntax"></a>語法

> **`/module:reference`** *`module-name=filename`*\
> **`/module:reference`** *`filename`*

### <a name="arguments"></a>引數

*`filename`*\
包含 *IFC 資料*之檔案的名稱，預建的模組資訊。 若要匯入多個模組，請針對每個檔案包含個別的 **`/module:reference`** 選項。

*`module-name`*\
匯出的主要模組介面單位名稱或完整模組分割區名稱的有效名稱。

## <a name="remarks"></a>備註

**`/module:reference`** 編譯器選項會要求您透過使用 [`/experimental:module`](experimental-module.md) 編譯器選項以及[/std： c + + 最新](std-specify-language-standard-version.md)選項來啟用實驗性模組支援。 從 Visual Studio 2019 16.8 版開始，可以使用此選項。

如果 **`/module:reference`** 引數不是 *`filename`* ，則會 *`module-name`* 在執行時間開啟檔案，以確認 *`filename`* 引數命名為特定的匯入。 在具有許多引數的案例中，它可能會導致執行時間效能變慢 **`/module:reference`** 。

*`module-name`* 必須是有效的主要模組介面單位名稱或完整模組磁碟分割名稱。 主要模組介面名稱的範例包括：

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

完整模組分割區名稱的範例包括：

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

如果使用來建立模組參考，則 *`module-name`* 如果編譯器遇到匯入該名稱，就不會搜尋命令列上的其他模組。 例如，假設有下列命令列：

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m=n.ifc
```

在上述案例中，如果編譯器看到， `import m;` 則 *`m.ifc`* 不會搜尋。

### <a name="examples"></a>範例

提供三個模組，如下表所示：

| 模組 | IFC 檔案 |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

使用引數的參考選項 *`filename`* 看起來可能像這樣：

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m-part.ifc /module:reference Networking.ifc
```

使用的參考選項如下所 *`module-name=filename`* 示：

```cmd
cl ... /experimental:module /module:reference m=m.ifc /module:reference M:Part1=m-part.ifc /module:reference Core.Networking=Networking.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式清單設定為 [**所有**設定]。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性，以加入 *`/module:reference`* 選項及其引數。 然後，選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。

## <a name="see-also"></a>另請參閱

[`/experimental:module` (啟用模組支援) ](experimental-module.md)\
[`/headerUnit` (使用標頭單位 IFC) ](headerunit.md)\
[`/module:exportHeader` (建立標頭單位) ](module-exportheader.md)\
[`/translateInclude` (將 include 指示詞轉譯為匯入指示詞) ](translateinclude.md)
