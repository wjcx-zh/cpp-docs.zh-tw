---
title: "宣告摘要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 85238c2cf07398bd74040a7d5d3c6c2e6a6b8fc3
ms.lasthandoff: 04/04/2017

---
# <a name="summary-of-declarations"></a>宣告摘要
`declaration`:  
 *declaration-specifiers attribute-seq* <sub>opt</sub> *init-declarator-list*<sub>opt</sub>**;**  
  
 /\* *attribute-seq* 是 Microsoft 專有 */  
  
 *declaration-specifiers*：  
 *storage-class-specifier declaration-specifiers*<sub>opt</sub>  
  
 *type-specifier declaration-specifiers*<sub>opt</sub>  
  
 *type-qualifier declaration-specifiers*<sub>opt</sub>  
  
 *attribute-seq*：            /\* *attribute-seq* 是 Microsoft 專有 \*/  
 *attribute attribute-seq* <sub>opt</sub>  
  
 *attribute*：其中一個      /* Microsoft 專有 \*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init-declarator-list*：  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*：  
 *declarator*  
  
 *declarator*  **=**  *initializer* /* 純量初始化 \*/  
  
 *storage-class-specifier*：  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec (**  *extended-decl-modifier-seq*  **)** /* Microsoft 專有 \*/  
  
 *type-specifier*：  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` /* Microsoft 專有 \*/  
  
 `__int16` /* Microsoft 專有 \*/  
  
 `__int32` /* Microsoft 專有 \*/  
  
 `__int64` /* Microsoft 專有 \*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *type-qualifier*：  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator*：  
 *identifier*  
  
 **(**  *declarator*  **)**  
  
 *direct-declarator*  **[**  *constant-expression* <sub>opt</sub>**]**  
  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* 新樣式的宣告子 \*/  
  
 *direct-declarator*  **(**  *identifier-list*<sub>opt</sub>**)** /* 已淘汰之樣式的宣告子 \*/  
  
 `pointer`:  
 **\*** *type-qualifier-list*<sub>opt</sub>  
  
 **\*** *type-qualifier-list*<sub>opt</sub>`pointer`  
  
 *parameter-type-list*：                           /\* 參數清單 \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list*：  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *type-qualifier-list*：  
 *type-qualifier*  
  
 *type-qualifier-list type-qualifier*  
  
 *enum-specifier*：  
 **enum**  *identifier*<sub>opt</sub>**{** *enumerator-list* **}**  
  
 **enum**  *identifier*  
  
 *enumerator-list*：  
 *enumerator*  
  
 *enumerator-list*  **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration-constant*  
  
 *enumeration-constant*  **=**  *constant-expression*  
  
 *enumeration-constant*：  
 *identifier*  
  
 *struct-or-union-specifier*：  
 *struct-or-union identifier*<sub>opt</sub>**{** *struct-declaration-list* **}** *struct-or-union identifier*  
  
 *struct-or-union*：  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*：  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 *struct-declaration*：  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list*：  
 *type-specifier specifier-qualifier-list*<sub>opt</sub>  
  
 *type-qualifier specifier-qualifier-list*<sub>opt</sub>  
  
 *struct-declarator-list*：  
 *struct-declarator struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator*：  
 *declarator*  
  
 *type-specifier declarator*<sub>opt</sub>**:** *constant-expression*  
  
 *parameter-declaration*：  
 *declaration-specifiers declarator* /* 具名宣告子 \*/  
  
 *declaration-specifiers abstract-declarator*<sub>opt</sub>**/\*** 匿名宣告子 **\*/**  
  
 *identifier-list*：**/\*** 適用於舊樣式宣告子 **\* /**  
 *identifier*  
  
 *identifier-list*  **,**  *identifier*  
  
 *abstract-declarator*：**/\***搭配匿名宣告子使用 **\*/**  
 *pointer*  
  
 `pointer`<sub>opt</sub>*direct-abstract-declarator*  
  
 *direct-abstract-declarator*：  
 **(**  *abstract-declarator*  **)**  
  
 *direct-abstract-declarator*<sub>opt</sub>**[** *constant-expression*<sub>opt</sub>**]**  
  
 *direct-abstract-declarator*<sub>opt</sub>**(** *parameter-type-list* <sub>opt</sub>**)**  
  
 *initializer*：  
 *assignment-expression*  
  
 **{**  *initializer-list*  **}** /* 適用於彙總初始化 \*/  
  
 **{**  *initializer-list*  **, }**  
  
 *initializer-list*：  
 *initializer*  
  
 *initializer-list*  **,**  *initializer*  
  
 *type-name*：  
 *specifier-qualifier-list abstract-declarator*<sub>opt</sub>  
  
 *typedef-name*：  
 *identifier*  
  
 *extended-decl-modifier-seq*：/\*   Microsoft 專有 \*/  
 *extended-decl-modifier*<sub>opt</sub>  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 *extended-decl-modifier*：   /\* Microsoft 專有 \*/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)   
 [階段結構文法](../c-language/phrase-structure-grammar.md)   
 [過時呼叫慣例](../cpp/obsolete-calling-conventions.md)
