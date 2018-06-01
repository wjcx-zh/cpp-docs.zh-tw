---
title: /Gd，/Gr，/Gv，/Gz （呼叫慣例） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3da8b4fcddbc384a785b27f0a7d706236a46ccf0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703768"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (呼叫慣例)
這些選項會決定函式引數會推入堆疊中，是否呼叫的函式的呼叫端函式從結尾的呼叫堆疊中移除引數的順序和編譯器用來識別的名稱裝飾慣例個別的函式。

## <a name="syntax"></a>語法

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>備註

**/Gd**、 預設值，指定[__cdecl](../../cpp/cdecl.md)函式和標記的函式，呼叫慣例的 c + + 成員除外的所有函式[__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)。

**/Gr**指定`__fastcall`呼叫慣例的 c + + 成員函式以外的所有函式，名為函式`main`，和函式標示為`__cdecl`， `__stdcall`，或`__vectorcall`。 所有`__fastcall`函式都必須有原型。 這個呼叫慣例僅供以 x86 為目標的編譯器，以及其他架構為目標的編譯器會忽略。

**/Gz**指定`__stdcall`呼叫慣例的 c + + 成員函式以外的所有函式，名為函式`main`，和函式標示為`__cdecl`， `__fastcall`，或`__vectorcall`。 所有`__stdcall`函式都必須有原型。 這個呼叫慣例僅供以 x86 為目標的編譯器，以及其他架構為目標的編譯器會忽略。

**/Gv**指定`__vectorcall`呼叫慣例的 c + + 成員函式以外的所有函式，名為的 main 函式、 函式與`vararg`變數引數清單或標示為衝突的函式`__cdecl`，`__stdcall`，或`__fastcall`屬性。 這個呼叫慣例只有使用支援 /arch:SSE2 的 x86 和 x64 架構和更高版本，且 ARM 架構為目標的編譯器會忽略。

接受可變數目的引數的函式必須標示為`__cdecl`。

**/Gd**， **/Gr**， **/Gv**和 **/Gz**與不相容[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)或 **/clr: pure**. **/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

> [!NOTE]
> 根據預設，適用於 x86 處理器，c + + 成員函式使用[__thiscall](../../cpp/thiscall.md)。

適用於所有處理器，成員函式，明確地標示為`__cdecl`， `__fastcall`， `__vectorcall`，或`__stdcall`會使用指定的呼叫慣例，如果它不會忽略在該架構上。 成員函式接受可變數目的引數一律會使用`__cdecl`呼叫慣例。

這些編譯器選項會有任何影響，在 c + + 方法和函式的裝飾名稱。 除非宣告為`extern "C"`，c + + 方法和函式使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。

如需有關呼叫慣例的詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

## <a name="cdecl-specifics"></a>__cdecl 細節

在 x86 上的處理器，所有函式引數會在堆疊上傳遞由右至左。 在 ARM 和 x64 架構中，某些引數會由暫存器中傳遞，其餘部分會在堆疊上傳遞由右至左。 呼叫常式會出現從堆疊的引數。

對於 C，`__cdecl`命名慣例是使用函式名稱加上底線 ( `_` ); 不會執行任何大小寫轉譯。 除非宣告為`extern "C"`，c + + 函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。

## <a name="fastcall-specifics"></a>__fastcall 細節

部分`__fastcall`函式的引數會傳遞暫存器中 (適用於 x86 處理器、 ECX 及 EDX)，以及其他會由右至左推入堆疊。 在傳回這些引數，從堆疊取出所呼叫的常式。 一般而言， **/Gr**減少執行時間。

> [!NOTE]
> 當您使用時請格外小心`__fastcall`內嵌組件語言撰寫的任何函式的呼叫慣例。 貴用戶使用暫存器可能會使用編譯器的衝突。

對於 C，`__fastcall`命名慣例是使用函式名稱前面加上 @ 記號 (`@`) 後面接著函式的引數，以位元組為單位的大小。 不是任何大小寫轉譯。 編譯器會使用此範本的命名慣例：

`@function_name@number`

當您使用`__fastcall`命名慣例，使用標準 include 檔案。 否則，您會收到未解析外部參考。

## <a name="stdcall-specifics"></a>__stdcall 細節

A`__stdcall`函式的引數會推入堆疊由右至左，和呼叫的函式會在它傳回之前將這些引數從堆疊取出。

對於 C，`__stdcall`命名慣例是使用函式名稱加上底線 ( `_` )，後面接著 at 符號 (@)，以及函式的引數，以位元組為單位的大小。 不會執行大小寫轉譯。 編譯器會使用此範本的命名慣例：

`_functionname@number`

## <a name="vectorcall-specifics"></a>__vectorcall 細節

A`__vectorcall`函式的整數引數傳遞的值，並使用最多兩個 （在 x86) 或 （在 x64) 的四個整數暫存器，以及最多六個 XMM 暫存器的浮點數和向量值以及其餘部分會在堆疊上傳遞由右至左。 在傳回呼叫的函式就會清除堆疊。 向量和浮點數的傳回值會在 XMM0 中傳回。

對於 C，`__vectorcall`命名慣例是使用函式名稱後面加上兩個 @ 符號 （@ @） 和函式的引數，以位元組為單位的大小。 不會執行大小寫轉譯。 編譯器會使用此範本的命名慣例：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**C/c + +** > **進階**屬性頁。

1. 修改**呼叫慣例**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。

## <a name="see-also"></a>另請參閱

- [編譯器選項](../../build/reference/compiler-options.md)
- [設定編譯器選項](../../build/reference/setting-compiler-options.md)
