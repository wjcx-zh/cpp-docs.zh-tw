---
title: /NXCOMPAT (與資料執行防止相容)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813314"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (與資料執行防止相容)

表示可執行檔是與 Windows 資料執行防止功能相容。

## <a name="syntax"></a>語法

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>備註

根據預設， **/NXCOMPAT**上。

**/Nxcompat: no**可用來明確指定為與資料執行防止不相容的可執行檔。

如需詳細資料執行防止的詳細資訊，請參閱下列文章：

- [資料執行防止 (DEP) 功能的詳細的說明](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [資料執行防止](/windows/desktop/Memory/data-execution-prevention)

- [資料執行防止 (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
