---
title: -Zp （結構成員對齊） |Microsoft 文件
ms.custom: ''
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1666da40f748d18c762eae19595692addcdbf78a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380858"
---
# <a name="zp-struct-member-alignment"></a>/Zp (結構成員對齊)

控制結構的成員會封裝為記憶體的方式，並指定在模組中的所有結構相同的封裝。

## <a name="syntax"></a>語法

> **/Zp**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>備註

當您指定 **/Zp**_n_選項，每個結構成員之後第一個儲存在成員類型的大小或*n*-位元組界限 (其中*n*是 1、 2、 4、 8 或 16)，兩者中較小。

下表說明可用的封裝的值：

|/Zp 引數|作用|
|-|-|
|1|1 位元組界限上封裝結構。 與相同 **/Zp**。|
|2|2 位元組界限上封裝結構。|
|4|4 位元組界限上封裝結構。|
|8|（預設值） 的 8 位元組界限上封裝結構。|
|16| 16 位元組界限上封裝結構。|

除非您有特定的對齊需求，您不應該使用此選項。

> [!WARNING]  
> Windows SDK 中的 c + + 標頭假設 **/Zp8**封裝。 如果，可能會發生損毀的記憶體 **/Zp**使用 Windows SDK 的標頭時，變更設定。

您也可以使用[套件](../../preprocessor/pack.md)來控制結構封裝。 如需對齊的詳細資訊，請參閱：

- [align](../../cpp/align-cpp.md)

- [__alignof 運算子](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [結構對齊範例](../../build/examples-of-structure-alignment.md)(x64 專用)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**C/c + +** > **程式碼產生**屬性頁。

1. 修改**結構成員對齊**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。

## <a name="see-also"></a>另請參閱

- [編譯器選項](../../build/reference/compiler-options.md)   
- [設定編譯器選項](../../build/reference/setting-compiler-options.md)
