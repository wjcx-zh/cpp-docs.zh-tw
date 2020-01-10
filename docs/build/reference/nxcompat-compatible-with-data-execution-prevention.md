---
title: /NXCOMPAT (與資料執行防止相容)
description: 描述 Microsoft C/C++ （MSVC）/NXCOMPAT 連結器選項，它會將可執行檔標記為與資料執行防止（DEP）相容。
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298983"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (與資料執行防止相容)

指出可執行檔與 Windows 資料執行防止功能相容。

## <a name="syntax"></a>語法

> **/NXCOMPAT**[ **： NO**]

## <a name="remarks"></a>備註

根據預設， **/NXCOMPAT**是 on。

**/NXCOMPAT： NO**可以用來將可執行檔明確指定為與資料執行防止不相容。

如需資料執行防止的詳細資訊，請參閱下列文章：

- [資料執行防止](/windows/win32/Memory/data-execution-prevention)

- [資料執行防止（Windows Embedded）](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇 [設定**屬性**] > **連結器** > [**命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入選項。 選擇 **[確定]** **或 [** 套用] 以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)
