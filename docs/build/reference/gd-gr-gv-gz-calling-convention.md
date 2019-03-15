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
ms.openlocfilehash: 7c4f7e6edb020f5c8d2abf80f14df33e18a915c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817459"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (呼叫慣例)

這些選項會決定在哪一個函式引數會推入堆疊，是否呼叫的函式的呼叫端函式從結尾的呼叫堆疊中移除引數的順序以及編譯器用來識別的名稱裝飾慣例個別的函式。

## <a name="syntax"></a>語法

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>備註

**/Gd**，預設值，指定[__cdecl](../../cpp/cdecl.md)呼叫慣例，所有函式，但是 c + + 成員函式和函式，會標示[__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)。

**/Gr**指定`__fastcall`呼叫慣例的 c + + 成員函式除外的所有函式，函式命名`main`，和函式，會標示`__cdecl`， `__stdcall`，或`__vectorcall`。 所有`__fastcall`函式都必須有原型。 這個呼叫慣例僅供以 x86 為目標的編譯器，並以其他架構為目標的編譯器會忽略。

**/Gz**指定`__stdcall`呼叫慣例的 c + + 成員函式除外的所有函式，函式命名`main`，和函式，會標示`__cdecl`， `__fastcall`，或`__vectorcall`。 所有`__stdcall`函式都必須有原型。 這個呼叫慣例僅供以 x86 為目標的編譯器，並以其他架構為目標的編譯器會忽略。

**/Gv**指定`__vectorcall`呼叫慣例的 c + + 成員函式除外的所有函式，名為的 main 的函式具有`vararg`變數引數清單或會標有衝突的函式`__cdecl`，`__stdcall`，或`__fastcall`屬性。 這個呼叫慣例只可用在支援/arch:sse2 的 x86 和 x64 架構上和更新版本，且 ARM 架構為目標的編譯器會忽略。

接受可變數目的引數的函式必須標記為`__cdecl`。

**/Gd**， **/Gr**， **/Gv**並 **/Gz**與不相容[/clr: safe](clr-common-language-runtime-compilation.md)或 **/clr: pure**. **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

> [!NOTE]
> 根據預設，適用於 x86 處理器，c + + 成員函式會使用[__thiscall](../../cpp/thiscall.md)。

適用於所有的處理器，明確地標示為成員函式`__cdecl`， `__fastcall`， `__vectorcall`，或`__stdcall`會使用指定的呼叫慣例，如果它不會忽略在該架構上。 成員函式接受可變數目的引數一律會使用`__cdecl`呼叫慣例。

這些編譯器選項會有任何作用，在 c + + 方法和函式的裝飾名稱。 除非宣告為`extern "C"`，c + + 方法和函式使用不同的名稱裝飾配置。 如需詳細資訊，請參閱 <<c0> [ 裝飾名稱](decorated-names.md)。

如需有關呼叫慣例的詳細資訊，請參閱 <<c0> [ 呼叫慣例](../../cpp/calling-conventions.md)。

## <a name="cdecl-specifics"></a>__cdecl 專屬資訊

在 x86 處理器而言，所有函數引數會都傳遞到堆疊上由右至左。 在 ARM 和 x64 架構，部分引數會傳遞由暫存器，其餘部分會由右至左傳遞到堆疊上。 呼叫的常式會取出來自堆疊的引數。

對於 C，`__cdecl`命名慣例是使用函式名稱加上底線 ( `_` ); 會執行任何大小寫轉譯。 除非宣告為`extern "C"`，c + + 函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱 <<c0> [ 裝飾名稱](decorated-names.md)。

## <a name="fastcall-specifics"></a>__fastcall 專屬資訊

某些`__fastcall`函式的引數會傳入暫存器 (適用於 x86 處理器上有 ECX 和 EDX)，以及其餘部分會由右至左推入堆疊。 它會傳回前，所呼叫的常式會取出這些引數由堆疊。 通常 **/Gr**會縮短執行時間。

> [!NOTE]
> 當您使用時要小心`__fastcall`內嵌組件語言所撰寫的任何函式的呼叫慣例。 暫存器的使用可能會使用編譯器的衝突。

對於 C，`__fastcall`命名慣例是使用函式名稱前面加上 at 符號 (**\@**) 後面跟著以位元組為單位的函式的引數的大小。 不是任何大小寫轉譯。 編譯器會使用此範本，做為命名慣例：

`@function_name@number`

當您使用`__fastcall`命名慣例，使用標準 include 檔案。 否則，您會得到未解析的外部參考。

## <a name="stdcall-specifics"></a>__stdcall 專屬資訊

A`__stdcall`函式的引數時，會推送至堆疊上，從右至左，和呼叫的函式會在返回前將這些引數由堆疊取出。

對於 C，`__stdcall`命名慣例是使用函式名稱加上底線 (**\_**)，後面接著 at 符號 (**\@**) 和函式的大小以位元組為單位的引數。 不會執行大小寫轉譯。 編譯器會使用此範本，做為命名慣例：

`_functionname@number`

## <a name="vectorcall-specifics"></a>__vectorcall 特定

A`__vectorcall`函式的整數引數傳遞的值，並使用最多兩個 （在 x86) 或 （在 x64) 的四個整數暫存器，以及六個 xmm 暫存器的浮點數和向量值和其餘部分會傳遞到堆疊上由右至左。 呼叫的函式會清除堆疊，它會傳回之前。 向量和浮點傳回值會在 XMM0 中傳回。

對於 C，`__vectorcall`命名慣例是使用函式名稱後面兩個 @ 符號 (**\@\@**) 和函式的引數，以位元組為單位的大小。 不會執行大小寫轉譯。 編譯器會使用此範本，做為命名慣例：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取  **C/c + +** > **進階**屬性頁。

1. 修改**呼叫慣例**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
