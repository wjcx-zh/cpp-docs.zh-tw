---
title: /Gd, /Gr, /Gv, /Gz (呼叫慣例)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
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
ms.openlocfilehash: e1617b7c158e9705a6211310fa7873f667a62ba5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234363"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (呼叫慣例)

這些選項會決定將函式引數推入堆疊的順序、呼叫端函式或呼叫的函式是否會在呼叫結尾從堆疊中移除引數，以及編譯器用來識別個別函式的名稱裝飾慣例。

## <a name="syntax"></a>語法

> **`/Gd`**\
> **`/Gr`**\
> **`/Gv`**\
> **`/Gz`**

## <a name="remarks"></a>備註

**`/Gd`** 預設設定會針對所有函式指定[__cdecl](../../cpp/cdecl.md)呼叫慣例，但 c + + 成員函式和函式除外，標記為[__stdcall](../../cpp/stdcall.md)、 [__fastcall](../../cpp/fastcall.md)或[__vectorcall](../../cpp/vectorcall.md)。

**`/Gr`** 指定所有函式的 **`__fastcall`** 呼叫慣例，但 c + + 成員函式、名為的函式， `main` 以及標記為 **`__cdecl`** 、或的函式除外 **`__stdcall`** **`__vectorcall`** 。 所有 **`__fastcall`** 函數都必須具有原型。 此呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略此呼叫慣例。

**`/Gz`** 指定所有函式的 **`__stdcall`** 呼叫慣例，但 c + + 成員函式、名為的函式， `main` 以及標記為 **`__cdecl`** 、或的函式除外 **`__fastcall`** **`__vectorcall`** 。 所有 **`__stdcall`** 函數都必須具有原型。 此呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略此呼叫慣例。

**`/Gv`** 指定所有函式的 **`__vectorcall`** 呼叫慣例，但 c + + 成員函式、名為的函式 `main` 、具有 `vararg` 變數引數清單的函式，或以衝突的 **`__cdecl`** 、 **`__stdcall`** 或 **`__fastcall`** 屬性標記的函式除外。 此呼叫慣例只可用在支援 /arch:SSE2 及更新版本的 x86 和 x64 架構上，以 ARM 架構為目標的編譯器會忽略此呼叫慣例。

接受引數數目的函式必須標記為 **`__cdecl`** 。

**`/Gd`**、 **`/Gr`** **`/Gv`** 和與 **`/Gz`** [`/clr:safe`](clr-common-language-runtime-compilation.md) 或 **/clr： pure**不相容。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。

> [!NOTE]
> 根據預設，針對 x86 處理器，c + + 成員函式會使用 [`__thiscall`](../../cpp/thiscall.md) 。

對於所有處理器而言，明確標示為、、或的成員函式會 **`__cdecl`** **`__fastcall`** **`__vectorcall`** **`__stdcall`** 使用指定的呼叫慣例（如果該架構上不會忽略）。 接受可變數目引數的成員函式一律會使用 **`__cdecl`** 呼叫慣例。

這些編譯器選項不影響 C++ 方法和函式的名稱裝飾。 除非宣告為 `extern "C"`，否則 C++方法和函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](decorated-names.md)。

如需有關呼叫慣例的詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

## <a name="__cdecl-specifics"></a>__cdecl 特性

在 x86 處理器上，所有函式引數會都由右至左地傳遞到堆疊上。 在 ARM 和 x64 架構上，部分引數會由暫存器傳遞，其餘部分會由右至左地傳遞到堆疊上。 呼叫常式會從堆疊取出引數。

對於 C， **`__cdecl`** 命名慣例會使用函式名稱，並在前面加上底線（ `_` ）; 不會執行任何案例轉譯。 除非宣告為 `extern "C"`，否則 C++函式會使用不同的名稱裝飾配置。 如需詳細資訊，請參閱[裝飾名稱](decorated-names.md)。

## <a name="__fastcall-specifics"></a>__fastcall 特性

部分函式 **`__fastcall`** 的引數會在暫存器中傳遞（適用于 x86 處理器、ECX 和 EDX），其餘部分則會從右至左推送至堆疊。 所呼叫的常式會在堆疊傳回之前，從堆疊中取出這些引數。 通常，**/Gr** 會縮短執行時間。

> [!NOTE]
> 當您針對以內嵌組解碼語言撰寫的任何函式使用呼叫慣例時，請務必小心 **`__fastcall`** 。 暫存器的使用可能會與編譯器的使用發生衝突。

對於 C， **`__fastcall`** 命名慣例會使用函式名稱，前面加上 @ 符號（ **\@** ），後面接著函數的引數大小（以位元組為單位）。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`@function_name@number`

當您使用 **`__fastcall`** 命名慣例時，請使用標準的 include 檔案。 否則，您會得到未解析的外部參考。

## <a name="__stdcall-specifics"></a>__stdcall 特性

函 **`__stdcall`** 式的引數會從右至左推送至堆疊，而被呼叫的函式會在傳回之前從堆疊中取出這些引數。

對於 C， **`__stdcall`** 命名慣例會使用函式名稱，前面加上底線（ **\_** ），後面接著 @ 符號（ **\@** ）和函式引數的大小（以位元組為單位）。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall 特性

函式 **`__vectorcall`** 的整數引數會以傳值方式傳遞，最多可使用兩個（x86）或四個（在 x64 上）整數暫存器，而且浮點和向量值最多6個 XMM 暫存器，其餘部分則由右至左傳遞至堆疊。 所呼叫的函式會在堆疊傳回前，將其清除。 向量和浮點會傳回在 XMM0 中傳回的值。

對於 C， **`__vectorcall`** 命名慣例會使用函式名稱，後面接著兩個 @ 符號（ **\@\@** ）和函式引數的大小（以位元組為單位）。 不會執行大小寫轉譯。 編譯器會使用此範本作為命名慣例：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [ **C/c + +**  >  **Advanced** ] 屬性頁。

1. 修改**呼叫慣例**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A> ＞。

## <a name="see-also"></a>另請參閱

- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
