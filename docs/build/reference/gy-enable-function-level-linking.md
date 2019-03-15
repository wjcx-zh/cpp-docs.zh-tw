---
title: /Gy (啟用函式階層連結)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 9643b8b4b4b26b3f7a8a59ed0085601b1a53094d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817968"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (啟用函式階層連結)

允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。

## <a name="syntax"></a>語法

```
/Gy[-]
```

## <a name="remarks"></a>備註

連結器會需要為來排除或排序 DLL 或.exe 檔案中的個別函式的 Comdat 函式個別封裝。

您可以使用連結器選項[/OPT （最佳化）](opt-optimizations.md)的.exe 檔案中排除未參考的封裝函式。

您可以使用連結器選項[/ORDER （Put 函式的順序）](order-put-functions-in-order.md)来包含的封裝函式中指定的順序中的.exe 檔案。

如果它們具現化呼叫，一律會封裝內嵌函式 (發生，例如，如果內嵌已關閉或需要為函式位址)。 此外，自動封裝在類別宣告中定義的 c + + 成員函式;其他函式則不會，並選取此選項需要將它們編譯為封裝函式。

> [!NOTE]
>  [/ZI](z7-zi-zi-debug-information-format.md)選項，用於編輯後繼續，會自動設定 **/Gy**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改**啟用函式層級連結**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
