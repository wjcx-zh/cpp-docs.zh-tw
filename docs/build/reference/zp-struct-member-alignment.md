---
title: /Zp (結構成員對齊)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: c78e670303bde68299725e18c6f588f5e410a971
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234298"
---
# <a name="zp-struct-member-alignment"></a>/Zp (結構成員對齊)

控制如何將結構的成員封裝到記憶體中，並為模組中的所有結構指定相同的封裝。

## <a name="syntax"></a>語法

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>備註

**`/ZpN`** 選項會指示編譯器儲存每個結構成員的位置。 編譯器會將成員儲存在成員類型大小較小的界限後面，或是*N*位元組的界限。

下表說明可用的封裝值：

|/Zp 引數|效果|
|-|-|
|1|在1個位元組的界限上封裝結構。 與相同 **`/Zp`** 。|
|2|在2個位元組的界限上封裝結構。|
|4|在4位元組界限上封裝結構。|
|8|封裝8位元組界限的結構（x86、ARM 和 ARM64 的預設值）。|
|16| 在16個位元組的界限上封裝結構（x64 的預設值）。|

除非您有特定的對齊需求，否則請不要使用此選項。

> [!WARNING]
> Windows SDK 集中的 c + + 標頭，並假設 **`/Zp8`** 在內部進行封裝。 如果 **`/Zp`** Windows SDK 標頭內的設定有所變更，可能會發生記憶體損毀。 標頭不 **`/Zp`** 會受到您在命令列上設定的任何選項所影響。

您也可以使用 [`pack`](../../preprocessor/pack.md) 控制結構封裝。 如需對齊的詳細資訊，請參閱：

- [`align`](../../cpp/align-cpp.md)

- [`alignof`操作](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN`（區段對齊）](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +** 程式  >  **代碼產生**] 屬性頁。

1. 修改**結構成員對齊**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md) \
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
