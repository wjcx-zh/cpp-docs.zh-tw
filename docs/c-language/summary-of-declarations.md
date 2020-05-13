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

*declaration*宣告：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*宣告規範*屬性-seq*<sub>opt</sub> *init-宣告子-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*屬性-seq* &nbsp; &nbsp; &nbsp; &nbsp; ：/ Microsoft 專有\*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*attribute* *attribute-seq*<sub>opt</sub>

*attribute* ： Microsoft 特定&nbsp; &nbsp; &nbsp; &nbsp; /的\*其中一個\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-宣告子-list***、***init-* 宣告子    

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*純量初始化的宣告子初始化*運算式*\*  / **=**    \*/

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**自動**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**參加**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**靜止**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec （** *延伸 extended-decl-modifier-seq-修飾詞-seq* **）**  / \* Microsoft 專有\*/

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**空位**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**短缺**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8**  / __int8\* Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16**  / __int16\* Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32**  / __int32\* Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64**  / __int64\* Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**前提**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**兩**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**簽署**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**經過**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct 或 union-規範*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉規範*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-名稱*

*類型-辨識符號*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**賦值**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**易變**

宣告*子：*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct-* 宣告子：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（** *declarator*宣告子 **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **[** *常數運算式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **（** *參數-類型清單* **）**  / \*新樣式的宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接*宣告子 **（** *識別碼清單*<sub>opt</sub> **）**  / \*過時樣式的宣告子\*/

*指標*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*類型-辨識符號-清單*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*類型-辨識符號-列出*<sub>opt</sub> *指標*

*參數-類型-清單*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ：&nbsp; &nbsp; &nbsp; &nbsp;參數清單&nbsp; &nbsp; / \*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* **，...**

*參數清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數-清單* **、** *參數*宣告

*type-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-辨識符號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*enum-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**列舉***識別碼*<sub>opt</sub> **{** *列舉值清單* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**列舉***識別碼*

*enumerator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉值*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉值清單* **，** *列舉值*

*列舉*值：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉-常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉常數* **=** *常數運算式*

*列舉常數*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*

*struct 或 union-規範*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構或等位**識別碼*<sub>opt</sub> **{** *結構聲明-清單* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union* *identifier*

*struct-or-union*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**結構**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**並**

*struct-declaration-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構聲明*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*結構聲明*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*結構*宣告子結構-宣告子 *-list* **、** *struct-* 宣告子

*結構聲明*子宣告子：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型規範* *declarator*宣告子<sub>opt</sub> **：** *常數運算式*

*parameter-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;宣告\*指定名稱宣告子*的* *declarator*  /宣告\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*宣告規範*抽象-* 宣告子<sub>opt</sub>  / \*匿名宣告子\*/

*識別碼-list*：/\*用於舊樣式的宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼-清單* **、** *識別碼*

*abstract-* 宣告子：\* /搭配匿名宣告子使用\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*滑鼠*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-abstract-declarator*

*direct-abstract-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（** *抽象-* 宣告子 **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-* 宣告子<sub>opt</sub> **[** *常數運算式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-* 宣告子<sub>opt</sub> **（** *參數類型-清單*<sub>opt</sub> **）**

*初始化運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指派-運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;用於匯總初始化的 **{** *初始化運算式-list* **}**  / \*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *初始化運算式-list* **，}**

*初始化運算式-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*初始設定式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*初始化運算式-list* **、** *初始化運算式*

*類型名稱*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*typedef-名稱*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*

*extended-extended-decl-modifier-seq-修飾詞-seq*：&nbsp; &nbsp; &nbsp; &nbsp; / \* Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*擴充-extended-decl-modifier-seq-修飾*詞&nbsp; &nbsp; &nbsp; &nbsp; / \* ： Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**執行緒**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>請參閱

[呼叫慣例](../cpp/calling-conventions.md)<br/>
[片語結構文法](../c-language/phrase-structure-grammar.md)<br/>
[過時的呼叫慣例](../cpp/obsolete-calling-conventions.md)
