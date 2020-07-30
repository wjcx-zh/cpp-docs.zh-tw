---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: 945202beca6c5deb525bd19886b947331f6f3ac3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228943"
---
# `__declspec`

**Microsoft 特定的**

用於指定儲存類別資訊的擴充屬性語法會使用 **`__declspec`** 關鍵字，這會指定特定類型的實例要與下列 Microsoft 特有的儲存類別屬性一起儲存。 其他儲存類別修飾詞的範例包括 **`static`** 和 **`extern`** 關鍵字。 不過，這些關鍵字是 C 和 C++ 語言的 ANSI 規格的一部分，因此擴充屬性語法未涵蓋它們。 擴充屬性語法可簡化並標準化 Microsoft 專有的 C 和 C++ 語言擴充功能。

## <a name="grammar"></a>文法

*extended-decl-modifier-seq-規範*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`**  *擴充-extended-decl-modifier-seq-修飾詞-seq*  **`)`**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*擴充-extended-decl-modifier-seq-修飾*詞*擴充-extended-decl-modifier-seq-修飾詞-seq*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`align(`** *#* **`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocate("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocator`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`appdomain`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`code_seg("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`deprecated`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`jitintrinsic`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noalias`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noinline`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noreturn`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`nothrow`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`novtable`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`process`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`property(`**{ **`get=`** _get_func_name_ &#124; **`,put=`** _put_func_name_ }**`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`restrict`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`safebuffers`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`selectany`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`spectre(nomitigation)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`uuid("`***ComObjectGUID***`")`**

空白字元會分隔宣告修飾詞序列。 範例會在後面的章節中顯示。

擴充屬性文法支援下列 Microsoft 特有的儲存類別屬性：、、、、、、、、、、、、、、、、、、、 [`align`](../cpp/align-cpp.md) [`allocate`](../cpp/allocate.md) [`allocator`](../cpp/allocator.md) [`appdomain`](../cpp/appdomain.md) [`code_seg`](../cpp/code-seg-declspec.md) [`deprecated`](../cpp/deprecated-cpp.md) [`dllexport`](../cpp/dllexport-dllimport.md) [`dllimport`](../cpp/dllexport-dllimport.md) [`jitintrinsic`](../cpp/jitintrinsic.md) [`naked`](../cpp/naked-cpp.md) [`noalias`](../cpp/noalias.md) [`noinline`](../cpp/noinline.md) [`noreturn`](../cpp/noreturn.md) [`nothrow`](../cpp/nothrow-cpp.md) [`novtable`](../cpp/novtable.md) [`process`](../cpp/process.md) [`restrict`](../cpp/restrict.md) [`safebuffers`](../cpp/safebuffers.md) [`selectany`](../cpp/selectany.md) [`spectre`](../cpp/spectre.md) 和 [`thread`](../cpp/thread.md) 。 它也支援下列 COM 物件屬性： [`property`](../cpp/property-cpp.md) 和 [`uuid`](../cpp/uuid-cpp.md) 。

、、、、、、、、、 **`code_seg`** **`dllexport`** **`dllimport`** **`naked`** **`noalias`** **`nothrow`** **`property`** **`restrict`** **`selectany`** **`thread`** 和 **`uuid`** 儲存類別屬性僅為套用它們之物件或函式的宣告屬性。 **`thread`** 屬性只會影響資料和物件。 **`naked`** 和 **`spectre`** 屬性只會影響函式。 **`dllimport`** 和 **`dllexport`** 屬性會影響函數、資料和物件。 **`property`**、 **`selectany`** 和**uu'id**屬性會影響 COM 物件。

為了與舊版相容， **`_declspec`** **`__declspec`** 除非指定了編譯器選項[/za \( 停用語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能，否則會是同義字。

**`__declspec`** 關鍵字應該放在簡單宣告的開頭。 編譯器會忽略在宣告 **`__declspec`** 中的 * 或 & 後面加上變數識別碼前方的任何關鍵字，而不會發出警告。

**`__declspec`** 在使用者自訂類型宣告的開頭指定的屬性會套用至該類型的變數。 例如：

```cpp
__declspec(dllimport) class X {} varX;
```

在本案例中，屬性會套用至 `varX`。 在 **`__declspec`** 或關鍵字之後放置的屬性會 **`class`** **`struct`** 套用至使用者定義型別。 例如：

```cpp
class __declspec(dllimport) X {};
```

在本案例中，屬性會套用至 `X`。

針對簡單宣告使用屬性的一般指導方針如下所示 **`__declspec`** ：

*extended-decl-modifier-seq-規範-seq* *init-宣告子-list*;

*Extended-decl-modifier-seq 規範-seq*應該包含基底型別（例如、、 **`int`** **`float`** **`typedef`** 或類別名稱）、儲存類別（例如 **`static`** ， **`extern`** ）或 **`__declspec`** 擴充功能，其中包括其他專案。 在其他專案中，init 宣告子*清單*應該包含宣告的指標部分。 例如：

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)
