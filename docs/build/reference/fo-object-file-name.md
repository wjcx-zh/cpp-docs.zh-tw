---
title: /Fo (目的檔名稱)
description: Visual Studio 中 Microsoft C++ /Fo(物件檔名)編譯器選項的參考指南。
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748969"
---
# <a name="fo-object-file-name"></a>/Fo (目的檔名稱)

指定要使用的物件*`.obj`*( ) 檔名或目錄,而不是預設值。

## <a name="syntax"></a>語法

> **`/Fo`**_路徑_

## <a name="remarks"></a>備註

可以使用**`/Fo`** 編譯器選項為 CL 編譯器命令生成的所有物件檔設置輸出目錄。 或者,您可以使用它重命名單個物件檔。

預設情況下,編譯器生成的物件檔將放置在當前目錄中。 它們被賦予源檔的基本名稱和*`.obj`* 副檔名。

要使用**`/Fo`** 選項重新命名物件檔,請指定輸出檔名作為*路徑名*參數。 重新命名物件檔案時,可以使用所需的任何名稱和副檔名,但建議的約定是*`.obj`* 使用 。 如果指定要編譯多個源檔時的檔名,**`/Fo`** 編譯器將生成命令行錯誤 D8036。

要使用**`/Fo`** 選項為 CL 命令建立的所有物件檔設定輸出目錄,請指定該目錄為*路徑名稱*參數。 目錄由*路徑名稱*參數中的尾隨斜杠指示。 指定的目錄必須存在;它不是自動創建的。

## <a name="example"></a>範例

以下命令列在驅動器 D 上的*\\*現有目錄 中間的中間值中創建名為*sample.obj*的物件檔。

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在可檢視化工作室中設定選項,或以程式設計方式設定選項

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**設定屬性** > **C/C++** > **輸出檔**屬性頁。

1. 修改**物件檔名**屬性以設置輸出目錄。 在 IDE 中,物件檔必須*`.obj`* 具有的 擴展名。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>＞。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
