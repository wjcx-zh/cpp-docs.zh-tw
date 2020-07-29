---
title: /GR (啟用執行階段類型資訊)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 974a2b38c793b21abc9f17f5b7ca5c9f5e3305f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215227"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (啟用執行階段類型資訊)

加入程式碼，以在執行時間檢查物件類型。

## <a name="syntax"></a>語法

```
/GR[-]
```

## <a name="remarks"></a>備註

當 **/GR**為 on 時，編譯器會定義 `_CPPRTTI` 預處理器宏。 根據預設， **/GR**是 on。 **/GR-** 會停用執行時間類型資訊。

如果編譯器無法以靜態方式解析程式代碼中的物件類型，請使用 **/GR** 。 當您的程式碼使用[Dynamic_cast 運算子](../../cpp/dynamic-cast-operator.md)或[typeid](../../cpp/typeid-operator.md)時，通常需要 **/GR**選項。 不過， **/GR**會增加影像的 .rdata 區段大小。 如果您的程式碼未使用 **`dynamic_cast`** 或 **`typeid`** ，則 **/GR-** 可能會產生較小的影像。

如需執行時間類型檢查的詳細資訊，請參閱*c + + 語言參考*中的[執行時間類型資訊](../../cpp/run-time-type-information.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [**語言**] 屬性頁。

1. 修改 [**啟用執行時間類型資訊**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
