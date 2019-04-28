---
title: /favor (專為架構最佳化)
ms.date: 11/04/2016
f1_keywords:
- /favor
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
ms.openlocfilehash: b914d3e6e7a2865ec610249ff51d320d7890adcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292818"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (專為架構最佳化)

**/favor:** `option`產生已最佳化，針對特定的架構，或為 AMD 和 Intel 架構中微-架構的程式碼。

## <a name="syntax"></a>語法

> **/favor:**{**blend** | **ATOM** | **AMD64** | **INTEL64**}

## <a name="remarks"></a>備註

**/favor:blend**<br/>
(x86 和 x64) 產生已為 AMD 和 Intel 架構中微架構特性最佳化的程式碼。 雖然 **/favor:blend**可能不會提供最佳的效能可能在特定處理器上，它設計來提供範圍廣泛的 x86 和 x64 處理器上的最佳效能。 根據預設， **/favor:blend**作用中。

**/favor:ATOM**<br/>
(x86 和 x64) 產生已為 Intel Atom 處理器和 Intel Centrino Atom 處理器技術特性最佳化的程式碼。 使用所產生的程式碼 **/favor:ATOM**可能也會產生 Intel SSSE3 SSE3、 mmx、sse、sse2 和 SSE 適用於 Intel 處理器的指示。

**/favor:AMD64**<br/>
(僅限 x64) 為 AMD Opteron 及支援 64 位元擴充功能的 Athlon 處理器，最佳化所產生的程式碼。 最佳化的程式碼可以在所有 x64 相容平台上執行。 使用所產生的程式碼 **/favor:AMD64**支援 Intel64 的 Intel 處理器上可能會導致較差的效能。

**/favor:INTEL64**<br/>
(僅限 x64) 最佳化為支援 Intel64 的 Intel 處理器所產生的程式碼，一般來說，會為該平台產生較佳效能。 所產生的程式碼可以在任何 x64 平台上執行。 程式碼，就會產生含有 **/favor:INTEL64** AMD Opteron 及支援 64 位元擴充功能的 Athlon 處理器上可能會導致較差的效能。

> [!NOTE]
> Intel64 架構先前稱為 Extended Memory 64 Technology 和對應的編譯器選項已 **/favor:EM64T**。

如需如何計劃適用於 x64 架構，請參閱[x64 軟體慣例](../x64-software-conventions.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取  **C /C++** 資料夾。

1. 選取 **命令列**屬性頁。

1. 輸入中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
