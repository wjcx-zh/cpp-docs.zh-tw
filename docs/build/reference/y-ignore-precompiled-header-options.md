---
title: /Y- (忽略先行編譯標頭檔選項)
ms.date: 11/04/2016
f1_keywords:
- /y-
helpviewer_keywords:
- Y- compiler option [C++]
- -Y- compiler option [C++]
- /Y- compiler option [C++]
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
ms.openlocfilehash: 7a823457b0d372527488e646f0d2fa83bd7a4740
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421515"
---
# <a name="y--ignore-precompiled-header-options"></a>/Y- (忽略先行編譯標頭檔選項)

所有其他原因`/Y`編譯器選項，以忽略 （而且無法本身會覆寫）。

## <a name="syntax"></a>語法

```
/Y-
```

## <a name="remarks"></a>備註

如需有關先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)

- [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
