---
title: /Os、/Ot (偏好小的程式碼、偏好快的程式碼)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: aa404641a42b0209e8436ca206e59a3b5f425133
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565954"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os、/Ot (偏好小的程式碼、偏好快的程式碼)

最小化或最大化 Exe 和 Dll 的大小。

## <a name="syntax"></a>語法

```
/Os
/Ot
```

## <a name="remarks"></a>備註

**/Os** （偏好小的程式碼） 將 Exe 和 Dll 的大小指示編譯器大小最佳化優先於速度降到最低。 編譯器可以減少許多 C 和 c + + 建構至機器碼的功能類似的序列。 有時候這些差異，提供大小與速度的權衡的取捨。 **/Os**並 **/Ot**選項可讓您指定哪一個喜好設定：

**/Ot** （偏好快的程式碼） 透過指示編譯器將優先於大小最大化的 Exe 和 Dll 的速度。 （這是預設值）。編譯器可以減少許多 C 和 c + + 建構至機器碼的功能類似的序列。 有時候，這些差異，提供大小與速度的權衡的取捨。 /Ot 選項隱含的最快速度 ([/o2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) 選項。 **/O2**選項結合數個選項可產生極快速的程式碼。

如果您使用 **/Os**或是 **/Ot**，則您也必須指定[/Og](../../build/reference/og-global-optimizations.md)最佳化程式碼。

> [!NOTE]
>  從分析測試回合所收集的資訊將會覆寫才會作用中您指定的最佳化 **/Ob**， **/Os**，或 **/Ot**。 如需詳細資訊，[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。

**x86 特定**

下列程式碼範例示範偏好小的程式碼之間的差異 (**/Os**) 選項和偏好快的程式碼 (**/Ot**) 選項：

> [!NOTE]
>  使用時，以下會說明預期的行為 **/Os**或是 **/Ot**。 不過，編譯器行為版本可能會導致不同的最佳化方式，如下列程式碼。

```
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

電腦的下列程式碼片段所示，DIFFER.c 編譯時的大小 (**/Os**)，編譯器實作乘法運算式傳回的陳述式中明確地乘法，以產生的程式碼的簡短但速度較慢順序：

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

或者，當 DIFFER.c 針對速度編譯 (**/Ot**)，編譯器實作乘法運算式中傳回的陳述式，為一系列的 shift 和`LEA`指令，以產生的程式碼的快速但時間較長序列：

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**結束 x86 特定**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **最佳化**屬性頁。

1. 修改**偏好大小或速度**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)