---
title: /Wp64 (偵測 64 位元可移植性問題)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: e5c30ac9096094948a83195f5b3990794c421685
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335879"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (偵測 64 位元可移植性問題)

這個編譯器選項已過時。 在 Visual Studio 2013 之前的 Visual Studio 版本中，這會在同時使用 [__w64](../../cpp/w64.md) 關鍵字標記的類型上，偵測到 64 位元可攜性問題。

## <a name="syntax"></a>語法

```
/Wp64
```

## <a name="remarks"></a>備註

預設情況下,在 Visual Studio 2013 之前的 Visual Studio 版本中 **,/Wp64**編譯器選項位於生成 32 位 x86 代碼的 MSVC 編譯器中,在生成 64 位 x64 代碼的 MSVC 編譯器中關閉。

> [!IMPORTANT]
> [/Wp64](wp64-detect-64-bit-portability-issues.md) 編譯器選項和 [__w64](../../cpp/w64.md) 關鍵字在 Visual Studio 2010 和 Visual Studio 2012 中已被取代，並且從 Visual Studio 2013 開始將不提供支援。 如果您轉換使用這個參數的專案，則在轉換期間將不會移轉參數。 若要在 Visual Studio 2010 或 Visual Studio 2012 中使用這個選項，您必須在專案屬性的 [命令列] **** 區段中，於 [其他選項] **** 下輸入編譯器參數。 如果您在命令列上使用 **/Wp64** 編譯器選項，則編譯器會發出命令列警告 D9002。 使用面向 64 位元平臺的 MSVC 編譯器並指定[/W4](compiler-option-warning-level.md)選項,而不是使用此選項和關鍵字來檢測 64 位元可移植性問題。 有關詳細資訊,請參閱[設定64 位 x64 目標的C++專案](../configuring-programs-for-64-bit-visual-cpp.md)。

您可以如同在 64 位元作業系統上使用下列類型的變數一樣，在 32 位元作業系統上對其進行測試：

- int

- long

- 指標

如果使用生成 64 位 x64 代碼的編譯器定期編譯應用程式,則只需在 32 位編譯中禁用 **/Wp64,** 因為 64 位編譯器將檢測所有問題。 有關如何定位 Windows 64 位元作業系統的詳細資訊,請參閱[設定 64 位元 x64 目標的C++專案](../configuring-programs-for-64-bit-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。

   如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 修改 [其他選項] **** 方塊，以包含 **/Wp64**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[設定適用於 64 位元、x64 目標的 C++ 專案](../configuring-programs-for-64-bit-visual-cpp.md)
