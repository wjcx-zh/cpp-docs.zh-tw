---
title: /Tc、/Tp、/TC、/TP (指定原始程式檔類型)
ms.date: 01/11/2018
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
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927636"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP (指定原始程式檔類型)

**/Tc**選項會指定其 filename 引數為 c 原始程式檔，即使它沒有 .c 副檔名也一樣。 **/Tp**選項會指定其 filename 引數為C++原始程式檔，即使它沒有 .cpp 或. .cxx 副檔名也一樣。 選項與檔案名之間的空格是選擇性的。 每個選項都會指定一個檔案;若要指定其他檔案，請重複選項。

**/Tc**和 **/tp**是 **/tc**和 **/tp**的全域變體。 它們會指定編譯器將命令列上名為的所有檔案視為 C 原始程式檔（ **/tc**）或C++原始程式檔（ **/tp**），而不考慮命令列上與選項相關的位置。 您可以使用 **/tc**或 **/tp**，在單一檔案上覆寫這些全域選項。

## <a name="syntax"></a>語法

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>引數

*filename*<br/>
C 或C++原始檔案。

## <a name="remarks"></a>備註

根據預設， **CL**會假設副檔名為 .c 的檔案是 c 原始程式檔，而副檔名為 .cpp 或. .cxx 的檔案是C++原始程式檔。

指定**TC**或**tc**選項時，會忽略[/Zc： Wchar_t （wchar_t 是原生類型）](zc-wchar-t-wchar-t-is-native-type.md)選項的任何規格。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > ] [**C/C++**   > Advanced] 屬性頁。

1. 修改 [**編譯為**] 屬性。 選擇 **[確定]** **或 [** 套用] 以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。

## <a name="examples"></a>範例

此 CL 命令列指定 prg 和 COLLATE prg 全部都是 C 原始程式檔。 CL 將無法辨識 PRINT. prg。

> CL MAIN。C/TcTEST.PRG/TcCOLLATE.PRG PRINT。PRG

此 CL 命令列指定 TEST1. c、TEST2. .cxx、TEST3 和 TEST4 會編譯為C++檔案，而 TEST5 則會編譯為 c 檔案。

> CL TEST1。C TEST2.CXX TEST3。TEST4。O/Tc TEST5。Z/TP

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
