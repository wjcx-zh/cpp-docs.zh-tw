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
ms.openlocfilehash: b158fb93cb5ea0b43124efe06edb53aebcc0d104
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425571"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (偵測 64 位元可移植性問題)

這個編譯器選項已過時。 在 Visual Studio 2013 之前的 Visual Studio 版本中，這會在同時使用 [__w64](../../cpp/w64.md) 關鍵字標記的類型上，偵測到 64 位元可攜性問題。

## <a name="syntax"></a>語法

```
/Wp64
```

## <a name="remarks"></a>備註

根據預設，在 Visual Studio 2013 之前的 Visual Studio 的版本 **/wp64**編譯器選項建置 32 位元 x86 的 Visual c + + 編譯器中處於關閉程式碼，並在 Visual c + + 編譯器建置的 64 位元、 x64 程式碼。

> [!IMPORTANT]
>  [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) 編譯器選項和 [__w64](../../cpp/w64.md) 關鍵字在 Visual Studio 2010 和 Visual Studio 2012 中已被取代，並且從 Visual Studio 2013 開始將不提供支援。 如果您轉換使用這個參數的專案，則在轉換期間將不會移轉參數。 若要在 Visual Studio 2010 或 Visual Studio 2012 中使用這個選項，您必須在專案屬性的 [命令列]  區段中，於 [其他選項]  下輸入編譯器參數。 如果您在命令列上使用 **/Wp64** 編譯器選項，則編譯器會發出命令列警告 D9002。 請改用以 64 位元平台為目標的 Visual C++ 編譯器，並指定 [/W4](../../build/reference/compiler-option-warning-level.md) 選項，而非使用這個選項和關鍵字來偵測 64 位元可攜性問題。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 64 位元 x64 目標](../../build/configuring-programs-for-64-bit-visual-cpp.md)。

您可以如同在 64 位元作業系統上使用下列類型的變數一樣，在 32 位元作業系統上對其進行測試：

- int

- long

- 指標

如果您經常使用建置 64 位元、 x64 編譯器編譯您的應用程式程式碼中，您可以只停用 **/wp64**在 32 位元編譯中因為 64 位元編譯器會偵測到的所有問題。 如需如何目標是 Windows 64 位元作業系統的詳細資訊，請參閱[設定 Visual c + + 64 位元 x64 目標](../../build/configuring-programs-for-64-bit-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。

   如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 修改 [其他選項]  方塊，以包含 **/Wp64**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[針對 64 位元 x64 目標設定 Visual C++](../../build/configuring-programs-for-64-bit-visual-cpp.md)
