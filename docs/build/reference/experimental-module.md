---
title: '/experimental: module (啟用模組支援)'
description: '使用/experimental: module 編譯器選項來啟用模組的實驗性編譯器支援。'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294455"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental: module (啟用模組支援)

啟用模組的實驗性編譯器支援, 如 draft c + + 20 標準所指定。

## <a name="syntax"></a>語法

> **/experimental: 模組**[ **-** ]

## <a name="remarks"></a>備註

您可以藉由使用 **/experimental: module**編譯器選項和[/std: c + + 最新](std-specify-language-standard-version.md)的選項來啟用實驗性模組支援。 您可以使用 **/experimental: module-** 明確停用模組支援。

從 Visual Studio 2015 Update 1 開始提供此選項。 從 Visual Studio 2019 版本 16.2, 在 Microsoft C++編譯器中, 不會完全實作為 c + + 20 Standard 模組的草稿。 您可以使用模組功能來建立單一資料分割模組, 並匯入 Microsoft 所提供的標準程式庫模組。 模組和使用它的程式碼必須使用相同的編譯器選項進行編譯。

如需模組以及如何使用和建立它們的詳細資訊, 請參閱[中C++的模組總覽](../../cpp/modules-cpp.md)。

以下是用來從來源檔案 ModuleName 建立匯出模組的編譯器命令列選項範例 *。 ixx*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 將 [設定] 下拉式選為 [**所有**設定]。

1. 選取 [設定**屬性** > ] [**C/C++**   > Language] 屬性頁。

1. 修改 [**啟用C++模組 (實驗性)** ] 屬性, 然後選擇 **[確定]** 。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
