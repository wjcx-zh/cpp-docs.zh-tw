---
title: -P （前置處理至檔案） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs:
- C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cbec53526fe90d1b4644b5b9fdd667d0fffcbe8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714502"
---
# <a name="p-preprocess-to-a-file"></a>/P (前置處理至檔案)

前置處理 C 和 c + + 原始程式檔，並將前置處理過的輸出寫入至檔案。

## <a name="syntax"></a>語法

```
/P
```

## <a name="remarks"></a>備註

檔案具有相同的基底名稱為來源檔案，以及.i 附加延伸模組。 在過程中，執行所有的前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[（保留註解在前置處理期間） 的 /C](../../build/reference/c-preserve-comments-during-preprocessing.md)連同選項 **/P**。

**/P**加入`#line`輸出中，開頭和結尾，每個包含的檔案以及環繞行，以移除前置處理器指示詞來進行條件式編譯指示詞。 這些指示詞重新編號前置處理過的檔案的行。 如此一來，後續階段的處理期間產生的錯誤，請參閱原始程式檔，而不是前置處理過的檔案中的行的行號。 若要隱藏的層代`#line`指示詞，使用[/EP （前置處理至 stdout 不 #line 指示詞）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ，以及 **/P**。

**/P**選項會抑制編譯。 它不會產生的.obj 檔案，即使您使用[/Fo （目的檔名稱）](../../build/reference/fo-object-file-name.md)。 您必須重新提交編譯的前置處理過的檔案。 **/P**也會隱藏輸出檔案，從 **/FA**， **/Fa**，和 **/Fm**選項。 如需詳細資訊，請參閱 < [/FA、 /Fa （清單檔）](../../build/reference/fa-fa-listing-file.md)並[/Fm （命名對應檔）](../../build/reference/fm-name-mapfile.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **前置處理器**屬性頁。

1. 修改**產生前置處理過的檔案**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>範例

下列命令列會前置處理`ADD.C`，保留註解，新增`#line`指示詞，並將結果寫入至檔案， `ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Fi (前置處理輸出檔名稱)](../../build/reference/fi-preprocess-output-file-name.md)