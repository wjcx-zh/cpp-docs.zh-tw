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
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328284"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (啟用函式階層連結)

允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。

## <a name="syntax"></a>語法

```
/Gy[-]
```

## <a name="remarks"></a>備註

連結器要求將函數單獨打包為 COMDAT,以排除 DLL 或 .exe 檔中的各個函數或排序各個函數。

您可以使用連結器選項[/OPT(優化)](opt-optimizations.md)從 .exe 檔中排除未引用的打包函數。

您可以使用連結器選項[/ORDER(按順序排列函數)](order-put-functions-in-order.md)在 .exe 檔案中按指定順序包含打包函數。

如果內聯函數被實例化為調用(例如,如果內聯已關閉或您獲取函數位址),則始終打包它們。 此外,C++類聲明中定義的成員函數將自動打包;其他函數不是,選擇此選項是將它們編譯為打包函數所必需的。

> [!NOTE]
> 用於編輯和繼續的[/ZI](z7-zi-zi-debug-information-format.md)選項會自動設置 **/Gy**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 單擊 **「代碼產生」** 屬性頁。

1. 修改**啟用函數級連結**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
