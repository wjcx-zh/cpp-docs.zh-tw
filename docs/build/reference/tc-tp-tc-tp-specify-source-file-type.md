---
title: /Tc、/Tp、/TC、/TP (指定原始程式檔類型)
ms.date: 1/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: f7ee51c858c9f90440cf0c2b21799ef7473cf6da
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813860"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP (指定原始程式檔類型)

**/Tc**選項會指定其檔名引數是 C 原始程式檔，即使它沒有副檔名為.c。 **/Tp**選項會指定其檔名引數是 c + + 原始程式檔，即使它沒有副檔名為.cpp 或.cxx 做。 選項和檔案名稱之間的空格是選擇性的。 每個選項會指定一個檔案;若要指定其他檔案，重複執行 選項。

**/TC**並 **/TP**是全域的變化 **/Tc**並 **/Tp**。 指定編譯器處理為 C 原始程式檔名為命令列上的所有檔案 (**/TC**) 或 c + + 原始程式檔 (**/TP**)，而不考慮與選項相關的命令列上的位置。 這些全域選項，可以藉由單一檔案的覆寫 **/Tc**或是 **/Tp**。

## <a name="syntax"></a>語法

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>引數

*filename*<br/>
C 或 c + + 原始程式檔。

## <a name="remarks"></a>備註

根據預設， **CL**假設副檔名為.c 檔案是 C 原始程式檔，並使用.cpp 或.cxx 副檔名的檔案是 c + + 原始程式檔。

時任一**TC**或**Tc**指定選項時，任何規格[/zc: wchar_t （wchar_t 是原生型別）](zc-wchar-t-wchar-t-is-native-type.md)選項會被忽略。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **進階**屬性頁。

1. 修改**編譯為**屬性。 選擇 **[確定]** 或是**套用**以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。

## <a name="examples"></a>範例

這個 CL 命令列指定 MAIN.c、 TEST.prg 和 COLLATE.prg 所有的 C 原始程式檔。 CL 將無法辨識 PRINT.prg。

> CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG

這個 CL 命令列指定 TEST1.c、 TEST2.cxx、 TEST3.huh 和 TEST4.o 會編譯為 c + + 檔案，而且 TEST5.z 編譯為 C 檔案。

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
