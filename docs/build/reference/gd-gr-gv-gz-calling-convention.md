---
title: /Gd, /Gr, /Gv, /Gz (呼叫慣例)
ms.date: 09/05/2018
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: eabb4e11715e03745e27911ccd654568d70b8352
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400504"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (呼叫慣例)

這些選項會決定將函式引數推入堆疊的順序、呼叫端函式或呼叫的函式是否會在呼叫結尾從堆疊中移除引數，以及編譯器用來識別個別函式的名稱裝飾慣例。

## <a name="syntax"></a>語法

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**

## <a name="remarks"></a>備註

根據預設， **/Gd** 會指定所有函式的 [__cdecl](../../cpp/cdecl.md) 呼叫慣例，但 C++ 成員函式和標記為 [__stdcall](../../cpp/stdcall.md)、[__fastcall](../../cpp/fastcall.md) 或 [__vectorcall](../../cpp/vectorcall.md) 的函式除外。

**/Gr** 會指定所有函式的 `__fastcall` 呼叫慣例，但 C++ 成員函式、名為 `main` 的函式和標記為 `__cdecl`、`__stdcall` 或 `__vectorcall` 的函式除外。 所有 `__fastcall` 函式都必須有原型。 此呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略此呼叫慣例。

**/Gz** 會指定所有函式的 `__stdcall` 呼叫慣例，但 C++ 成員函式、名為 `main` 的函式和標記為 `__cdecl`、`__fastcall` 或 `__vectorcall` 的函式除外。 所有 `__stdcall` 函式都必須有原型。 此呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略此呼叫慣例。

**/Gv**指定`__vectorcall`以外的所有函式的呼叫慣例C++成員函式、 函式`main`，與函式`vararg`變數引數清單或會標有衝突的函式`__cdecl`， `__stdcall`，或`__fastcall`屬性。 此呼叫慣例只可用在支援 /arch:SSE2 及更新版本的 x86 和 x64 架構上，以 ARM 架構為目標的編譯器會忽略此呼叫慣例。

函式若接受可變數目的引數，則必須標示為 `__cdecl`。

**/Gd**、 **/Gr**、 **/Gv** 和 **/Gz** 都與 [/clr: safe](clr-common-language-runtime-compilation.md) 或 **/clr: pure** 不相容。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。

> [!NOTE]
> 根據預設，x86 處理器的 C++ 成員函式會使用 [__thiscall](../../cpp/thiscall.md)。

針對所有處理器，明確標示為 `__cdecl`、`__fastcall`、`__vectorcall` 或 `__stdcall` 的成員函式會使用指定的呼叫慣例，但前提是此慣例不會在該架構上遭到忽略。 若成員函式接受可變數目的引數，則一律會使用 `__cdecl` 呼叫慣例。

這些編譯器選項不影響 C++ 方法和函式的名稱裝飾。 除非宣告為 `extern "C"`，否則 C++方法和函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](decorated-names.md)。

如需有關呼叫慣例的詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

## <a name="cdecl-specifics"></a>__cdecl 特性

在 x86 處理器上，所有函式引數會都由右至左地傳遞到堆疊上。 在 ARM 和 x64 架構上，部分引數會由暫存器傳遞，其餘部分會由右至左地傳遞到堆疊上。 呼叫常式會從堆疊取出引數。

對於 C 語言，`__cdecl` 命名慣例會使用前面加上底線的 (`_`) 的函式名稱；不會執行任何大小寫轉譯。 除非宣告為 `extern "C"`，否則 C++函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](decorated-names.md)。

## <a name="fastcall-specifics"></a>__fastcall 特性

`__fastcall` 函式的某些引數會傳入暫存器 (適用於 x86 處理器、ECX 和 EDX)，而其餘部分會由右至左地推入堆疊。 所呼叫的常式會在堆疊傳回之前，從堆疊中取出這些引數。 通常， **/Gr** 會縮短執行時間。

> [!NOTE]
> 當您對以內嵌組件語言所撰寫的任何函式使用 `__fastcall` 呼叫慣例時，應格外小心。 暫存器的使用可能會與編譯器的使用發生衝突。

對於 C 語言，`__fastcall` 命名慣例會使用前面加上 at 符號 ( **\@** ) 的函式名稱，而後面會接著以位元組為單位的函式引數大小。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`@function_name@number`

當您使用 `__fastcall` 命名慣例時，請使用標準的 include 檔案。 否則，您會得到未解析的外部參考。

## <a name="stdcall-specifics"></a>__stdcall 特性

`__stdcall` 函式的引數會從右至左地推送到堆疊上，而所呼叫的常式會在堆疊傳回之前，從堆疊中取出這些引數。

對於 C 語言，`__stdcall` 命名慣例會使用前面加上底線 ( **\_** ) 的函式名稱，而後面會接著 at 符號 ( **\@** ) 和以位元組為單位的函式引數大小。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`_functionname@number`

## <a name="vectorcall-specifics"></a>__vectorcall 特性

`__vectorcall` 函式的整數引數會以值來傳遞，並使用最多兩個 (在 x86 上) 或四個 (在 x64 上) 整數暫存器，以及針對浮點和向量值使用最多六個 XMM 暫存器，其餘部分則由右至左地傳遞到堆疊上。 所呼叫的函式會在堆疊傳回前，將其清除。 向量和浮點會傳回在 XMM0 中傳回的值。

對於 C 語言，`__vectorcall` 命名慣例會使用後面加上兩個 at 符號 ( **\@\@** ) 的函式名稱，且後方還會加上以位元組為單位的函式引數大小。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [C/C++]   > [進階]  屬性頁。

1. 修改**呼叫慣例**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
