---
title: -V （版本號碼） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ad42a72a874537a6307cfc547852f812f4aaaa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707963"
---
# <a name="v-version-number"></a>/V (版本號碼)

已取代。 .Obj 檔案中內嵌的文字字串。

## <a name="syntax"></a>語法

```
/Vstring
```

## <a name="arguments"></a>引數

*string*<br/>
字串，指定要內嵌的.obj 檔案中的版本號碼或著作權注意事項。

## <a name="remarks"></a>備註

Stringcan 標籤的 版本號碼或著作權注意事項的.obj 檔案中。 任何空格或定位字元的字元必須括在雙引號 （"），如果是字串的一部分。 反斜線 (\\) 前面必須加上任何雙引號如果它們是字串的一部分。 之間的空格 **/V**和`string`是選擇性的。

您也可以使用[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md)編譯器註解型別引數，將編譯器名稱和版本號碼.obj 檔案中。

**/V**選項已被取代，開始在 Visual Studio 2005;**/V**做主要是用來支援建置虛擬裝置驅動程式 (Vxd)，並建置 VxDs 已不再支援 Visual c + + 工具組。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。

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