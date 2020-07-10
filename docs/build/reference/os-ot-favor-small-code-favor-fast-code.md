---
title: /Os、/Ot (偏好小的程式碼、偏好快的程式碼)
description: MSVC 編譯器選項/Os 和/Ot 指定優化程式碼時是否偏好大小或速度。
ms.date: 07/08/2020
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
ms.openlocfilehash: 384019ddf7b80b8dd4e00197d73d1e4ac536634c
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180821"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>`/Os`， `/Ot` (偏好小型程式碼，偏好快速的程式碼) 

將 Exe 和 Dll 的大小最小化或最大化。

## <a name="syntax"></a>語法

> **`/Os`**\
> **`/Ot`**

## <a name="remarks"></a>備註

**`/Os`** (偏好小型程式碼) 藉由指示編譯器比速度更快，將 Exe 和 Dll 的大小降到最低。 編譯器可以將許多 C 和 c + + 結構減少為功能類似的機器碼序列。 這些差異偶爾會提供大小與速度的取捨。 **`/Os`** 和 **`/Ot`** 選項可讓您指定其中一個的喜好設定：

**`/Ot`** (偏好快速的程式碼) 藉由指示編譯器比大小更快，讓 Exe 和 Dll 的速度發揮到最大。 **`/Ot`** 這是啟用優化時的預設值。 編譯器可以將許多 C 和 c + + 結構減少為功能類似的機器碼序列。 這些差異偶爾會提供大小與速度的取捨。 [ **`/Ot`** [`/O2`](o1-o2-minimize-size-maximize-speed.md) (最大化速度) ] 選項會隱含選項。 **`/O2`** 選項結合了數個選項，以產生更快速的程式碼。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫在您指定、或時，將會生效的任何優化 **`/Ob`** **`/Os`** **`/Ot`** 。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。

### <a name="x86-specific-example"></a>x86 特定範例

下列範例程式碼示範 (偏好小型程式 **`/Os`** 代碼) 選項和 (偏好快速程式 **`/Ot`** 代碼) 選項之間的差異：

> [!NOTE]
> 此範例說明使用或時的預期 **`/Os`** 行為 **`/Ot`** 。 不過，從發行到發行版本的編譯器行為可能會導致下列程式碼的不同優化。

```c
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

如以下的機器碼片段所示，當編譯成 *`differ.c`* size () 時，編譯器會 **`/Os`** 明確地將 return 語句中的乘法運算式實作為乘法，以產生簡短但較慢的程式碼序列：

```asm
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

或者， *`differ.c`* 針對速度 () 編譯時 **`/Ot`** ，編譯器會將 return 語句中的乘法運算式實作為一系列的 shift 和 `LEA` 指示，以產生快速但較長的程式碼序列：

```asm
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **優化**] 屬性頁。

1. 修改偏好**大小或速度**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A> ＞。

## <a name="see-also"></a>另請參閱

[/O 選項 (將程式碼最佳化)](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
