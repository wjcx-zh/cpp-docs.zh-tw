---
title: '-EP （前置處理至 stdout 不 #line 指示詞） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598c202cbac0176cb77243c7f0f891ef94c3dcc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714879"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (前置處理至 stdout 不加 #line 指示詞)

前置處理 C 和 c + + 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。

## <a name="syntax"></a>語法

```
/EP
```

## <a name="remarks"></a>備註

在過程中，執行所有的前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[（保留註解在前置處理期間） 的 /C](../../build/reference/c-preserve-comments-during-preprocessing.md)選項搭配 **/EP**。

**/EP**選項會抑制編譯。 您必須重新提交編譯的前置處理過的檔案。 **/EP**也會隱藏輸出檔案，從 **/FA**， **/Fa**，和 **/Fm**選項。 如需詳細資訊，請參閱 < [/FA、 /Fa （清單檔）](../../build/reference/fa-fa-listing-file.md)並[/Fm （命名對應檔）](../../build/reference/fm-name-mapfile.md)。

前置處理過的檔案，而不是原始程式檔的行號，請參閱後面的階段中的處理期間產生的錯誤。 如果您想要參考原始的來源檔案行號，請使用[/E （前置處理至 stdout）](../../build/reference/e-preprocess-to-stdout.md)改。 **/E**選項會增加`#line`指示詞，可針對此目的的輸出。

若要將前置處理過的輸出中，使用`#line`指示詞檔案中，使用[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項。

若要將前置處理過的輸出傳送到 stdout 中,，使用`#line`指示詞，使用 **/P**並 **/EP**一起。

您無法使用先行編譯標頭 **/EP**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **前置處理器**屬性頁。

1. 修改**產生前置處理過的檔案**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>範例

下列命令列會前置處理檔案`ADD.C`、 保留註解，並且將結果顯示標準輸出裝置上：

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)