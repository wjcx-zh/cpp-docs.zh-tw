---
title: __declspec |Microsoft 文件
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c610da3545e7269c307542930140616dc6af9dce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="declspec"></a>__declspec

**Microsoft 特定的**

指定儲存類別資訊使用的擴充的屬性語法 **__declspec**關鍵字，指定要與下面所列的 Microsoft 專有儲存類別屬性儲存在給定類型的執行個體。 其他儲存類別修飾詞的範例包括**靜態**和**extern**關鍵字。 不過，這些關鍵字是 C 和 C++ 語言的 ANSI 規格的一部分，因此擴充屬性語法未涵蓋它們。 擴充屬性語法可簡化並標準化 Microsoft 專有的 C 和 C++ 語言擴充功能。

## <a name="grammar"></a>文法

*宣告規範*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**deprecated**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**process**  
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**thread**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

空白字元會分隔宣告修飾詞序列。 範例會在後面的章節中顯示。

擴充的屬性文法支援這些 Microsoft 專有儲存類別屬性：[對齊](../cpp/align-cpp.md)，[配置](../cpp/allocate.md)， [appdomain](../cpp/appdomain.md)， [code_seg](../cpp/code-seg-declspec.md)，[取代](../cpp/deprecated-cpp.md)， [dllexport](../cpp/dllexport-dllimport.md)， [dllimport](../cpp/dllexport-dllimport.md)， [jitintrinsic](../cpp/jitintrinsic.md)， [naked](../cpp/naked-cpp.md)， [noalias](../cpp/noalias.md)， [noinline](../cpp/noinline.md)， [noreturn](../cpp/noreturn.md)， [nothrow](../cpp/nothrow-cpp.md)， [novtable](../cpp/novtable.md)[程序](../cpp/process.md)，[限制](../cpp/restrict.md)， [safebuffers](../cpp/safebuffers.md)， [selectany](../cpp/selectany.md)， [spectre](../cpp/spectre.md)，和[執行緒](../cpp/thread.md)。 它也支援這些 COM 物件屬性：[屬性](../cpp/property-cpp.md)和[uuid](../cpp/uuid-cpp.md)。

**Code_seg**， **dllexport**， **dllimport**， **naked**， **noalias**， **nothrow**，**屬性**，**限制**， **selectany**，**執行緒**，和**uuid**儲存類別屬性是只的物件或他們要套用至函式的宣告屬性。 **執行緒**屬性會影響資料，而且僅限物件。 **Naked**和**spectre**屬性會影響只有函式。 **Dllimport**和**dllexport**屬性會影響函式、 資料和物件。 **屬性**， **selectany**，和**uuid**屬性會影響 COM 物件。

**__Declspec**關鍵字應該放置在簡單宣告的開頭。 編譯器會忽略，而無任何警告 **__declspec**關鍵字後面 * 或 & 和在宣告中變數的識別項前面。

A **__declspec**中使用者定義型別宣告的開頭指定的屬性會套用至該類型的變數。 例如: 

```cpp
__declspec(dllimport) class X {} varX;
```

在本案例中，屬性會套用至 `varX`。 A **__declspec**屬性會放**類別**或**結構**關鍵字套用至使用者定義類型。 例如: 

```cpp
class __declspec(dllimport) X {};
```

在本案例中，屬性會套用至 `X`。

一般使用方針 **__declspec**簡單宣告的屬性如下所示：

*seq 規範 decl 功能* *init 宣告子清單*;

*Decl-規範 seq*應該包含在其他方面，基底類型 (例如**int**， **float**、 **typedef**，或類別名稱)，儲存類別 (例如**靜態**， **extern**)，或 **__declspec**延伸模組。 *Init 宣告子清單*應該包含在其他方面，宣告的指標部分。 例如: 

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

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)  
[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)  
