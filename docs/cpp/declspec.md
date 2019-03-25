---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e924f3e4a038f900e084dbf84d85430d815c8e8f
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416945"
---
# <a name="declspec"></a>__declspec

**Microsoft 專屬**

指定儲存類別資訊使用的擴充的屬性語法 **__declspec**關鍵字，指定給定型別的執行個體是所儲存的下面所列的 Microsoft 專有儲存類別屬性。 其他儲存類別修飾詞的範例包括**靜態**並**extern**關鍵字。 不過，這些關鍵字是 C 和 C++ 語言的 ANSI 規格的一部分，因此擴充屬性語法未涵蓋它們。 擴充屬性語法可簡化並標準化 Microsoft 專有的 C 和 C++ 語言擴充功能。

## <a name="grammar"></a>文法

*宣告規範*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocator**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**deprecated**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**process**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**

空白字元會分隔宣告修飾詞序列。 範例會在後面的章節中顯示。

擴充的屬性文法支援這些 Microsoft 專有儲存類別屬性：[對齊](../cpp/align-cpp.md)，[配置](../cpp/allocate.md)，[配置器](../cpp/allocator.md)， [appdomain](../cpp/appdomain.md)， [code_seg](../cpp/code-seg-declspec.md)，[取代](../cpp/deprecated-cpp.md)， [dllexport](../cpp/dllexport-dllimport.md)， [dllimport](../cpp/dllexport-dllimport.md)， [jitintrinsic](../cpp/jitintrinsic.md)， [naked](../cpp/naked-cpp.md)， [noalias](../cpp/noalias.md)， [noinline](../cpp/noinline.md)， [noreturn](../cpp/noreturn.md)， [nothrow](../cpp/nothrow-cpp.md)，[novtable](../cpp/novtable.md)，[程序](../cpp/process.md)，[限制](../cpp/restrict.md)， [safebuffers](../cpp/safebuffers.md)， [selectany](../cpp/selectany.md)， [spectre](../cpp/spectre.md)，並[執行緒](../cpp/thread.md)。 它也支援這些 COM 物件的屬性：[屬性](../cpp/property-cpp.md)並[uuid](../cpp/uuid-cpp.md)。

**Code_seg**， **dllexport**， **dllimport**， **naked**， **noalias**， **nothrow**，**屬性**，**限制**， **selectany**，**執行緒**，以及**uuid**儲存類別屬性是只宣告物件或函式套用至屬性。 **執行緒**屬性會影響資料，而且只有物件。 **Naked**並**spectre**屬性會影響僅函式。 **Dllimport**並**dllexport**屬性會影響函式、 資料和物件。 **屬性**， **selectany**，並**uuid**屬性會影響 COM 物件。

為了與舊版中，相容性 **_declspec**同義 **__declspec**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)是指定此項目。

**__Declspec**關鍵字應該放置在簡單的宣告的開頭。 編譯器會忽略，不顯示任何警告 **__declspec**關鍵字後面 * 或 & 和變數宣告中的識別項前面。

A **__declspec**中使用者定義型別宣告的開頭指定的屬性會套用至該類型的變數。 例如: 

```cpp
__declspec(dllimport) class X {} varX;
```

在本案例中，屬性會套用至 `varX`。 A **__declspec**屬性會放**類別**或是**結構**關鍵字套用至使用者定義型別。 例如: 

```cpp
class __declspec(dllimport) X {};
```

在本案例中，屬性會套用至 `X`。

一般使用方針 **__declspec**簡單宣告的屬性如下所示：

*decl-specifier-seq* *init-declarator-list*;

*Decl-modifier-規範-seq*應該包含在其他方面，基底型別 (例如**int**， **float**，則**typedef**，或類別名稱)，儲存類別 (例如**靜態**， **extern**)，或有 **__declspec**延伸模組。 *Init 宣告子清單*應該包含在其他方面，宣告的指標部分。 例如: 

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)