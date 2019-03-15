---
title: /vmm、-vms、-vmv （一般用途表示）
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 7a46cecdbf96ad891ce218df4769a60590e562a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810038"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm、/vms、/vmv (一般用途表示)

使用的時機[/vmb、 /vmg （表示方法）](vmb-vmg-representation-method.md)當做[表示方法](vmb-vmg-representation-method.md)。 這些選項會指出尚未發現的類別定義的繼承模型。

## <a name="syntax"></a>語法

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>備註

請參閱下表描述的選項。

|選項|描述|
|------------|-----------------|
|**/vmm**|指定要使用多重繼承類別的成員指標的最常見的表示。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和 引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)會**multiple_inheritance**。<br /><br /> 此表示法大於，所需的單一繼承。<br /><br /> 如果宣告為其成員指標類別定義的繼承模型是虛擬的則編譯器會產生錯誤。|
|**/vms**|指定要使用沒有繼承 」 或 「 單一繼承類別的成員指標的最常見的表示。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和 引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)會**single_inheritance**。<br /><br /> 這是指標的類別的最小的可能表示成員。<br /><br /> 如果宣告為其成員指標類別定義的繼承模型為多重或虛擬的編譯器會產生錯誤。|
|**/vmv**|指定要使用虛擬繼承類別的成員指標的最常見的表示。 它永遠不會造成錯誤，並為預設值。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和 引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)會**virtual_inheritance**。<br /><br /> 此選項需要較大的指標和額外的程式碼來解譯指標比其他選項。|

當您指定其中一個繼承模型選項時，該模型用於對類別成員，不論其繼承型別或指標是否宣告之前或之後之類別的所有指標中。 因此，如果您總是使用單一繼承類別時，您可以減少程式碼大小以進行編譯 **/vms**; 不過，如果您想要使用最常見的案例 （但會犧牲的最大的資料表示法），進行編譯 **/vmv**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/vmb、/vmg (表示方法)](vmb-vmg-representation-method.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
