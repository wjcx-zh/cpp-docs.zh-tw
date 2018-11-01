---
title: /NXCOMPAT (與資料執行防止相容)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 815719468e7dcf9325d19efe879b8f4ace040094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490489"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (與資料執行防止相容)

表示可執行檔是與 Windows 資料執行防止功能相容。

## <a name="syntax"></a>語法

> **/NXCOMPAT**[**: NO**]

## <a name="remarks"></a>備註

根據預設， **/NXCOMPAT**上。

**/Nxcompat: no**可用來明確指定為與資料執行防止不相容的可執行檔。

如需詳細資料執行防止的詳細資訊，請參閱下列文章：

- [資料執行防止 (DEP) 功能的詳細的說明](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [資料執行防止](/windows/desktop/Memory/data-execution-prevention)

- [資料執行防止 (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
