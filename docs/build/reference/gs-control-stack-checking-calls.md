---
title: /Gs (控制堆疊檢查呼叫)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: 49433cd0c84b05248bacf1e930dd5ec78bc3cd1b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418824"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (控制堆疊檢查呼叫)

控制堆疊探查的臨界值。

## <a name="syntax"></a>語法

> **/Gs**[*size*]

## <a name="arguments"></a>引數

*size*<br/>
(選擇性) 在起始堆疊探查之前，本機變數可佔用的位元組數目。 不允許有空格之間 **/Gs**並*大小*。

## <a name="remarks"></a>備註

A*堆疊探查*是一連串的函式呼叫的開始處的編譯器插入的程式碼。 起始時，堆疊探查會良性地進入記憶體，深入達到存放函式本機變數所需的空間量。 這會導致作業系統以透明的方式如有需要，其餘的函式執行之前，其他的堆疊記憶體頁面。

根據預設，編譯器產生的程式碼會在函式需要超過一頁的堆疊空間時，起始堆疊探查。 這相當於編譯器選項 **/Gs4096**適用於 x86、 x64、 ARM、 及 ARM64 平台。 這個值允許應用程式和 Windows 記憶體管理員動態地在執行階段增加認可給程式堆疊的記憶體數量。

> [!NOTE]
> 預設值 **/Gs4096**可讓 Windows 在執行階段正確地成長的應用程式的程式堆疊。 我們建議您不要變更預設值，除非您確實知道為何必須變更它。

有些程式—例如虛擬裝置驅動程式—不需要這項預設的堆疊成長機制。 在這種情況下，堆疊探查不需要，您可以停止產生設定編譯器*大小*大於任何函式將會需要存放本機變數的值。

**/ Gs0**起始堆疊探查，每個函式呼叫的本機變數需要的儲存體。 這對效能可能會產生負面影響。

適用於 x64 目標，如果 **/Gs**指定的選項，但沒有*大小*引數，它相當於 **/Gs0**。 如果*大小*引數是 1 到 9，就會發出警告 D9014，效果等同於指定 **/Gs0**。

適用於 x86，ARM，和 ARM64 目標 **/Gs**選項，但沒有*大小*引數是相同 **/Gs4096**。 如果*大小*引數是 1 到 9，就會發出警告 D9014，效果等同於指定 **/Gs4096**。

對於所有目標而言*大小*介於 10 到 2147485647 的引數設定的臨界值，以指定的值。 A*大小*的嚴重錯誤 C1049 2147485648 或更高的原因。

您可以使用，以開啟或關閉的堆疊探查[check_stack](../../preprocessor/check-stack.md)指示詞。 **/Gs**而`check_stack`pragma 在標準 C 程式庫常式沒有效果; 它們會影響您編譯的函式。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 請輸入 **/Gs**編譯器選項，以及選擇性大小**其他選項**。 選擇 **[確定]** 或是**套用**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
