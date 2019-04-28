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
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315907"
---
# <a name="zp-struct-member-alignment"></a>/Zp (結構成員對齊)

控制結構的成員會封裝到記憶體的方式，並指定在模組中的所有結構相同的封裝。

## <a name="syntax"></a>語法

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>備註

**/Zp**_n_選項會告訴編譯器儲存每個結構成員的位置。 編譯器在較小的成員類型的大小的界限上的第一個儲存成員或*n*-位元組的界限。

下表說明可用的封裝值：

|/Zp 引數|作用|
|-|-|
|1|1 位元組界限上封裝結構。 與相同 **/Zp**。|
|2|2 位元組界限上封裝結構。|
|4|4 位元組界限上封裝結構。|
|8|（預設值適用於 x86 ARM 及 ARM64） 的 8 位元組界限上封裝結構。|
|16| （適用於 x64 的預設值） 的 16 位元組界限上封裝結構。|

請勿使用此選項，除非您有特定的對齊需求。

> [!WARNING]
> C++Windows SDK 中的標頭設定，並假設 **/zp8**內部封裝。 如果，可能會發生損毀的記憶體 **/Zp**設定已變更的 Windows SDK 標頭內。 標頭不會受到任何 **/Zp**您在命令列設定的選項。

您也可以使用[組件](../../preprocessor/pack.md)來控制結構的封裝。 如需對齊的詳細資訊，請參閱：

- [align](../../cpp/align-cpp.md)

- [__alignof 運算子](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN (區段記憶體對齊)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **產生程式碼**屬性頁。

1. 修改**結構成員對齊**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md) \
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
