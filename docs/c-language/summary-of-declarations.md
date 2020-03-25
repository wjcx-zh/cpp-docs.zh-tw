---
title: 宣告摘要
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170432"
---
# <a name="summary-of-declarations"></a>宣告摘要

*宣告*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;宣告 *-規範* *屬性-seq*<sub>opt</sub> *init-宣告子-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*儲存類別*指定名稱宣告 *-* 規範<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-規範*宣告 *-* 指定名稱<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-限定詞*宣告 *-* 規範<sub>opt</sub>

*屬性-seq* ：&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*屬性* *屬性-seq*<sub>opt</sub>

*屬性*：其中一個&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 特定的 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall __based](../cpp/stdcall.md) [__fastcall __thiscall](../cpp/based-grammar.md) [__cdecl __inline](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__vectorcall](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-* 宣告子-清單 **，** *init-* 宣告子

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告子*<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;宣告*子 **=** *初始化運算式* /純量初始化 \* \*    /

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**註冊**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**靜態**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**外部**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec （** *擴充-extended-decl-modifier-seq-修飾詞-seq* **）**  /\* Microsoft 特定 \*/

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-qualifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *直接-* 宣告子

*direct-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **（** *declarator*宣告子 **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接-* 宣告子 **[** *常數運算式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接-* 宣告子 **（** *參數-類型清單* **）**  /\* 新樣式的宣告子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接*宣告子宣告子 **（** *識別碼清單*<sub>opt</sub> **）**  /\* 過時樣式的宣告子 \*/

*pointer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *類型-辨識符號清單*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *類型-辨識符號清單*<sub>opt</sub> *指標*

*parameter-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* The parameter list \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* **...**

*parameter-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數-清單* **，** *參數聲明*

*type-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-辨識符號-清單* *類型-辨識符號*

*enum-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**列舉***識別碼*<sub>opt</sub> **{** *列舉值清單* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**列舉***識別碼*

*enumerator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉程式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉值清單* **，** *列舉值*

*列舉程式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉-常數* **=** *常數運算式*

*enumeration-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*struct-or-union-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構或等位* *識別碼*<sub>opt</sub> **{** *結構聲明-清單* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構或聯集* *識別碼*

*struct-or-union*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構聲明-列出* *結構*宣告

*struct-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*規範-辨識符號-列出* *結構-宣告子清單* **;**

*specifier-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-規範* *規範-辨識符號-清單*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-辨識符號* *規範-辨識符號-清單*<sub>opt</sub>

*struct-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構*宣告子結構-宣告子 *-list* **、** *struct-* 宣告子

*struct-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-規範* *declarator*宣告子<sub>opt</sub> **：** *常數運算式*

*parameter-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;宣告 *-* 規範宣告子 /\* 命名宣告*子 \*/*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;宣告 *-* 規範*抽象-* 宣告子<sub>opt</sub> /\* 匿名宣告子 \*/

*identifier-list*: /\* For old-style declarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼-清單* **、** *識別碼*

*abstract-declarator*: /\* Used with anonymous declarators \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *直接-抽象-* 宣告子

*direct-abstract-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **（** *抽象-* 宣告子 **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-* 宣告子<sub>opt</sub> **[** *常數運算式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-* 宣告子<sub>opt</sub> **（** *參數-類型清單*<sub>opt</sub> **）**

*initializer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** 初始化*運算式-list* **}**  /\* 匯總初始化 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *初始化運算式-list* **，}**

*initializer-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*初始化運算式-清單* **、** *初始化運算式*

*type-name*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*規範-限定詞-列出* *抽象-* 宣告子<sub>opt</sub>

*typedef-name*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*擴充-extended-decl-modifier-seq-修飾詞-seq*：&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq-修飾詞-seq* *擴充-extended-decl-modifier-seq-修飾*詞

*擴充-extended-decl-modifier-seq-修飾*詞：&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**執行緒**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)<br/>
[階段結構文法](../c-language/phrase-structure-grammar.md)<br/>
[過時呼叫慣例](../cpp/obsolete-calling-conventions.md)
