---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180221"
---
# <a name="__declspec"></a>__declspec

**Microsoft 專屬**

用於指定儲存類別資訊的擴充屬性語法會使用 **__declspec**關鍵字，這會指定特定類型的實例要與下列 Microsoft 特有的儲存類別屬性一起儲存。 其他儲存類別修飾詞的範例包括**static**和**extern**關鍵字。 不過，這些關鍵字是 C 和 C++ 語言的 ANSI 規格的一部分，因此擴充屬性語法未涵蓋它們。 擴充屬性語法可簡化並標準化 Microsoft 專有的 C 和 C++ 語言擴充功能。

## <a name="grammar"></a>文法

*extended-decl-modifier-seq-規範*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec （** *擴充-extended-decl-modifier-seq-修飾詞-seq* **）**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*擴充-extended-decl-modifier-seq-修飾*詞*擴充-extended-decl-modifier-seq-修飾詞-seq*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**對齊（** *#* **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**配置（"** *segname* **"）**<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;配置**器<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg （"** *segname* **"）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;已**淘汰**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;程式**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**屬性（** { **get =** _get_func_name_ &#124; **，put =** _put_func_name_ } **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**限制**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre （nomitigation）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**執行緒**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uuid （"** *ComObjectGUID* **"）**

空白字元會分隔宣告修飾詞序列。 範例會在後面的章節中顯示。

擴充屬性文法支援這些 Microsoft 特有的儲存類別屬性： [align](../cpp/align-cpp.md)、 [allocate](../cpp/allocate.md)、配置[器](../cpp/allocator.md)、 [appdomain](../cpp/appdomain.md)、 [code_seg](../cpp/code-seg-declspec.md)、已被[取代](../cpp/deprecated-cpp.md)、 [dllexport](../cpp/dllexport-dllimport.md)、 [dllimport](../cpp/dllexport-dllimport.md)、 [jitintrinsic](../cpp/jitintrinsic.md)、 [naked](../cpp/naked-cpp.md)、 [noalias](../cpp/noalias.md)、 [noinline](../cpp/noinline.md)、 [noreturn](../cpp/noreturn.md)、 [nothrow](../cpp/nothrow-cpp.md)、 [novtable](../cpp/novtable.md)、 [process](../cpp/process.md)、 [restrict](../cpp/restrict.md)、 [safebuffers](../cpp/safebuffers.md)、 [selectany](../cpp/selectany.md)、 [spectre](../cpp/spectre.md)和[thread](../cpp/thread.md)。 它也支援下列 COM 物件屬性： [property](../cpp/property-cpp.md)和[uuid](../cpp/uuid-cpp.md)。

**Code_seg**、 **dllexport**、 **dllimport**、 **naked**、 **noalias**、 **nothrow**、 **property**、 **restrict**、 **selectany**、 **thread**和**uuid**儲存類別屬性，只是其套用物件或函式之宣告的屬性。 **Thread**屬性只會影響資料和物件。 **Naked**和**spectre**屬性只會影響函式。 **Dllimport**和**dllexport**屬性會影響函數、資料和物件。 **屬性**、 **selectany**和**uuid**屬性會影響 COM 物件。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_declspec**是 **__declspec**的同義字。

**__Declspec**關鍵字應該放在簡單宣告的開頭。 編譯器會忽略在宣告中的 * 或 & 後面加上變數識別碼前方的任何 **__declspec**關鍵字，而不會發出警告。

在使用者自訂類型宣告的開頭指定的 **__declspec**屬性會套用至該類型的變數。 例如：

```cpp
__declspec(dllimport) class X {} varX;
```

在本案例中，屬性會套用至 `varX`。 在**class**或**struct**關鍵字之後放置的 **__declspec**屬性會套用至使用者定義型別。 例如：

```cpp
class __declspec(dllimport) X {};
```

在本案例中，屬性會套用至 `X`。

使用簡單宣告的 **__declspec**屬性的一般指導方針如下所示：

*extended-decl-modifier-seq-規範-seq* *init-宣告子-list*;

*Extended-decl-modifier-seq 規範-seq*應該包含基底型別（例如**int**、 **float**、 **typedef**或類別名稱）、儲存類別（例如**static**、 **extern**）或 **__declspec**延伸模組。 在其他專案中，init 宣告子*清單*應該包含宣告的指標部分。 例如：

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)
