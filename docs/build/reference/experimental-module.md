---
title: '/experimental： module (Enable module support) '
description: 使用/experimental： module 編譯器選項可啟用模組的實驗性編譯器支援。
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 0eea5127f651eaff30c197271ae6da38ac1356be
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075721"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental： module (Enable module support) 

啟用模組的實驗性編譯器支援（如 draft c + + 20 標準所指定）。

## <a name="syntax"></a>語法

> **/experimental： module**[ **-** ]

## <a name="remarks"></a>備註

您可以使用 **/experimental： module** 編譯器選項以及 [/std： c + + 最新](std-specify-language-standard-version.md) 選項來啟用實驗性模組支援。 您可以使用 **/experimental： module-** 明確停用模組支援。

從 Visual Studio 2015 Update 1 開始，可以使用此選項。 從 Visual Studio 2019 16.2 版中，Draft c + + 20 標準模組未在 Microsoft c + + 編譯器中完整執行。 您可以使用 [模組] 功能來建立單一資料分割模組，以及匯入 Microsoft 所提供的標準程式庫模組。 模組和使用它的程式碼必須使用相同的編譯器選項進行編譯。

如需模組的詳細資訊，以及如何使用和建立模組的詳細資訊，請參閱 [c + + 中的模組總覽](../../cpp/modules-cpp.md)。

以下是編譯器命令列選項的範例，用來從來源檔案 ModuleName 建立匯出模組 *ixx*：

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. **將 [設定**] 下拉式清單設定為 [**所有**設定]。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **語言**] 屬性頁。

1. 修改 [ **啟用 c + + 模組 (實驗性) ** ] 屬性，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[`/headerUnit` (使用標頭單位 IFC) ](headerunit.md)\
[`/module:exportHeader` (建立標頭單位) ](module-exportheader.md)\
[`/module:reference` (使用命名模組 IFC) ](module-reference.md)\
[`/translateInclude` (將 include 指示詞轉譯為匯入指示詞) ](translateinclude.md)\
[/Zc (一致性)](zc-conformance.md)
