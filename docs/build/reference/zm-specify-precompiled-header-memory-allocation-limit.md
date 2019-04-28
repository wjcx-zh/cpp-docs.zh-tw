---
title: /Zm (指定先行編譯標頭檔的記憶體配置上限)
ms.date: 03/08/2019
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: 09df8e1ee9a97289e29e1191e8c1585580435b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315270"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (指定先行編譯標頭檔的記憶體配置上限)

判斷編譯器配置來建構先行編譯標頭檔的記憶體量。

## <a name="syntax"></a>語法

```
/Zmfactor
```

## <a name="arguments"></a>引數

*factor*<br/>
縮放比例，可決定編譯器用來建構先行編譯標頭檔的記憶體量。

*因素*引數是編譯器定義之工作緩衝區預設大小的百分比。 預設值*因素*為 100 （百分比），但是您可以指定較大或較小的金額。

## <a name="remarks"></a>備註

在 Visual Studio 2015 之前, 的版本C++編譯器會使用數個離散堆積，而且每個有有限度的限制。 目前，編譯器能夠動態成長至總堆積大小的限制，必要時，堆積，並允許先行編譯標頭組成多個位址範圍。 因此， **/Zm**編譯器選項會很少會需要。

如果編譯器堆積空間不足，並發出[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)當您使用錯誤訊息 **/Zm**編譯器選項時，您可能保留過多記憶體。 請考慮移除 **/Zm**選項。

如果編譯器發出[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)錯誤訊息，則伴隨[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)訊息會指出*因素*引數，以使用當您重新編譯使用 **/Zm**編譯器選項。 這只是訊息重要時使用先行編譯標頭`#pragma hdrstop`。 在其他情況下，將會假性錯誤起因於 Windows 虛擬記憶體不足的壓力問題和建議使用 **/Zm**選項應予忽略。 相反地，請考慮使用時，減少平行處理序數目 **/maxcpucount** MSBUILD 的選項。搭配 EXE **/MP** CL 選項。EXE。 如需詳細資訊，請參閱 <<c0> [ 先行編譯標頭 (PCH) 問題和建議](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

下表顯示如何*因素*引數會影響記憶體配置限制，如果您假設預設值先行編譯標頭緩衝區的大小為 75 MB。

|值*因素*|記憶體配置限制|
|-----------------------|-----------------------------|
|10|7.5 MB|
|100|75 MB|
|200|150 MB|
|1000|750 MB|
|2000|1500 MB|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>設定記憶體配置限制的其他方法

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 /Zm 編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 在 [導覽] 窗格中，選取**組態屬性** > **C /C++** > **命令列**。

1. 請輸入 **/Zm**中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-the-zm-compiler-option-programmatically"></a>以程式設計方式設定 /Zm 編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
