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
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336179"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os、/Ot (偏好小的程式碼、偏好快的程式碼)

最小化或最大化 EXEs 和 DLL 的大小。

## <a name="syntax"></a>語法

```
/Os
/Ot
```

## <a name="remarks"></a>備註

**/O(** 有利於小代碼)通過指示編譯器選擇大小而不是速度來最小化 EXEs 和 DLL 的大小。 編譯器可以減少許多 C 和 C++構造,以在功能上相似的計算機代碼序列。 有時,這些差異會提供大小與速度的權衡。 **/O**與 **/Ot**選項允許您指定一個偏好設定而不是另一個偏好設定:

**/Ot(** 希望快速代碼)透過指示編譯器選擇速度而不是大小來最大化 EXEs 和 DLL 的速度。 (這是預設值。編譯器可以減少許多 C 和 C++構造,以在功能上相似的計算機代碼序列。 有時,這些差異會提供大小與速度的權衡。 **/Ot**選項由"最大化速度 ([/O2](o1-o2-minimize-size-maximize-speed.md)) 「選項隱含。 **/O2**選項結合了多個選項,可生成非常快的代碼。

如果使用 **/O**或 **/Ot**,則還必須指定[/Og](og-global-optimizations.md)以最佳化代碼。

> [!NOTE]
> 從分析測試運行中收集的資訊將覆蓋如果指定 **/Ob、/O**或 **/Os****/Ot**時生效的優化。 關於詳細資訊,[設定檔開機化 。](../profile-guided-optimizations.md)

**x86 專屬資訊**

以下範例代碼展示「首選小代碼 (**/O)** 選項與「首選快速代碼 (**/Ot**) 」選項之間的區別:

> [!NOTE]
> 下面描述了使用 **/O**或 **/Ot**時的預期行為。 但是,從發佈到發佈的編譯器行為可能會導致對以下代碼進行不同的優化。

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

如下圖所示,當為大小 **(/O)** 編譯為*S.c 時,編譯器在 return 語句中顯式實現乘法表達式,以生成短但較慢的程式碼序列:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

或者,當為速度 **(/Ot)** 編譯 DIFFER.c 時,編譯器將返回語句中的乘法運算式實現`LEA`為一系列移 位元和指令,以生成快速但較長的程式碼序列:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**結束 x86 特定**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按下 **「優化**屬性」 頁。

1. 修改 **"優惠大小"或"速度"** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>＞。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
