---
title: '/headerUnit (使用標頭單位 IFC) '
description: 使用/headerUnit 編譯器選項可指定要在目前編譯中匯入的現有 IFC 標頭單位。
ms.date: 09/13/2020
f1_keywords:
- /headerUnit
helpviewer_keywords:
- /headerUnit
- Use header unit IFC
ms.openlocfilehash: 2734df728b188dcfbbe5f475cfc67715a070975d
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079071"
---
# <a name="headerunit-use-header-unit-ifc"></a>`/headerUnit` (使用標頭單位 IFC) 

告知編譯器將可匯入標頭名稱的指示詞轉譯為指示詞 `#include` `import header-name;` ，而不是使用文字包含。

## <a name="syntax"></a>語法

> **`/headerUnit`** *`header-filename`*=*`ifc-filename`*

### <a name="arguments"></a>引數

*`header-filename`*\
編譯器將解析成的檔案名 `header-name` 。 在編譯器中，會將檔案 `import header-name ;` 解析 `header-name` 為磁片上的某些檔案。 使用 *`header-filename`* 指定該檔案。 一旦相符之後，編譯器會開啟名為的對應 IFC *`ifc-filename`* 以進行匯入。

*`ifc-filename`*\
包含 *IFC 資料*之檔案的名稱，預建的模組資訊。 若要匯入多個標頭單位，請 **`/headerUnit`** 為每個檔案包含個別的選項。

## <a name="remarks"></a>備註

**`/headerUnit`** 編譯器選項會要求您透過使用 [`/experimental:module`](experimental-module.md) 編譯器選項以及[/std： c + + 最新](std-specify-language-standard-version.md)選項來啟用實驗性模組支援。 從 Visual Studio 2019 16.8 版開始，可以使用此選項。

編譯器無法對應單一 *`header-name`* 至多個 IFC 檔案。 雖然可以將多個 *`header-name`* 引數對應至單一 IFC，但我們不建議這樣做。 IFC 的內容會匯入，就像只是指定的標頭一樣 *`header-name`* 。

### <a name="examples"></a>範例

假設有一個專案參考兩個標頭檔和其標頭單位，如下表所列：

| 標頭檔 | IFC 檔案 |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

參考這些特定標頭檔之標頭單位的編譯器選項，可能看起來像這個範例：

```CMD
cl ... /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式清單設定為 [**所有**設定]。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 修改 [ **其他選項** ] 屬性，以加入 *`/headerUnit`* 選項和引數。 然後，選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。

## <a name="see-also"></a>另請參閱

[`/experimental:module` (啟用模組支援) ](experimental-module.md)\
[`/module:exportHeader` (建立標頭單位) ](module-exportheader.md)\
[`/module:reference` (使用命名模組 IFC) ](module-reference.md)\
[`/translateInclude` (將 include 指示詞轉譯為匯入指示詞) ](translateinclude.md)\
