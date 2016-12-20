---
title: "宣告摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 宣告摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`declaration`:  
 *declaration\-specifiers attribute\-seq*  opt *init\-declarator\-list* opt**;**  
  
 \/\* *attribute\-seq* 是 Microsoft 專有 \*\/  
  
 *declaration\-specifiers*：  
 *storage\-class\-specifier declaration\-specifiers* opt  
  
 *type\-specifier declaration\-specifiers* opt  
  
 *type\-qualifier declaration\-specifiers* opt  
  
 *attribute\-seq* :            \/\* *attribute\-seq* 是 Microsoft 專有 \*\/  
 *attribute attribute\-seq* opt  
  
 *attribute* : one of      \/\* Microsoft 專有 \*\/  
 ||||  
|-|-|-|  
|[\_\_asm](../assembler/inline/asm.md)|[\_\_clrcall](../cpp/clrcall.md)|[\_\_stdcall](../cpp/stdcall.md)|  
|[\_\_based](../cpp/based-grammar.md)|[\_\_fastcall](../cpp/fastcall.md)|[\_\_thiscall](../cpp/thiscall.md)|  
|[\_\_cdecl](../cpp/cdecl.md)|[\_\_inline](../misc/inline-inline-forceinline.md)|[\_\_vectorcall](../cpp/vectorcall.md)|  
  
 *init\-declarator\-list*:  
 *init\-declarator*  
  
 *init\-declarator\-list*  **,**  *init\-declarator*  
  
 *init\-declarator*:  
 *宣告子*  
  
 *declarator*  **\=**  *initializer* \/\* 純量初始化 \*\/  
  
 *storage\-class\-specifier*：  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **\_\_declspec \(**  *extended\-decl\-modifier\-seq*  **\)** \/\* Microsoft 專有 \*\/  
  
 *type\-specifier*：  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` \/\* Microsoft 專有 \*\/  
  
 `__int16` \/\* Microsoft 專有 \*\/  
  
 `__int32` \/\* Microsoft 專有 \*\/  
  
 `__int64` \/\* Microsoft 專有 \*\/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 *type\-qualifier*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer` opt *direct\-declarator*  
  
 *direct\-declarator*:  
 *識別項*  
  
 **\(**  *declarator*  **\)**  
  
 *direct\-declarator*  **\[**  *constant\-expression*  opt **\]**  
  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)** \/\* 新樣式的宣告子 \*\/  
  
 *direct\-declarator*  **\(**  *identifier\-list* opt **\)** \/\* 過時樣式的宣告子 \*\/  
  
 `pointer`:  
 **\*** *type\-qualifier\-list* opt  
  
 **\*** *type\-qualifier\-list* opt `pointer`  
  
 *parameter\-type\-list*:                           \/\* 參數清單 \*\/  
 *parameter\-list*  
  
 *parameter\-list* **, ...**  
  
 *parameter\-list*:  
 *參數宣告*  
  
 *parameter\-list*  **,**  *parameter\-declaration*  
  
 *type\-qualifier\-list*:  
 *type\-qualifier*  
  
 *type\-qualifier\-list type\-qualifier*  
  
 *enum\-specifier*:  
 **enum**  *identifier* opt **{** *enumerator\-list* **}**  
  
 **enum**  *identifier*  
  
 *enumerator\-list*:  
 *列舉程式*  
  
 *enumerator\-list*  **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration\-constant*  
  
 *enumeration\-constant*  **\=**  *constant\-expression*  
  
 *enumeration\-constant*:  
 *識別項*  
  
 *struct\-or\-union\-specifier*:  
 *struct\-or\-union identifier* opt **{** *struct\-declaration\-list* **}** *struct\-or\-union identifier*  
  
 *struct\-or\-union*:  
 **struct**  
  
 **union**  
  
 *struct\-declaration\-list*:  
 *struct\-declaration*  
  
 *struct\-declaration\-list struct\-declaration*  
  
 *struct\-declaration*:  
 *specifier\-qualifier\-list struct\-declarator\-list*  **;**  
  
 *specifier\-qualifier\-list*:  
 *type\-specifier specifier\-qualifier\-list* opt  
  
 *type\-qualifier specifier\-qualifier\-list* opt  
  
 *struct\-declarator\-list*:  
 *struct\-declarator struct\-declarator\-list*  **,**  *struct\-declarator*  
  
 *struct\-declarator*:  
 *宣告子*  
  
 *type\-specifier declarator* opt **:** *constant\-expression*  
  
 *parameter\-declaration*:  
 *declaration\-specifiers declarator* \/\* 具名宣告子 \*\/  
  
 *declaration\-specifiers abstract\-declarator* opt **\/\*** 匿名宣告子 **\*\/**  
  
 *identifier\-list*: **\/\*** 適用於舊樣式宣告子 **\* \/**  
 *識別項*  
  
 *identifier\-list*  **,**  *identifier*  
  
 *abstract\-declarator*: **\/\*** 搭配匿名宣告子使用 **\*\/**  
 *指標*  
  
 `pointer` opt *direct\-abstract\-declarator*  
  
 *direct\-abstract\-declarator*:  
 **\(**  *abstract\-declarator*  **\)**  
  
 *direct\-abstract\-declarator* opt **\[** *constant\-expression* opt **\]**  
  
 *direct\-abstract\-declarator* opt **\(** *parameter\-type\-list* opt **\)**  
  
 *initializer*:  
 *assignment\-expression*  
  
 **{**  *initializer\-list*  **}** \/\* 適用於彙總初始化 \*\/  
  
 **{**  *initializer\-list*  **, }**  
  
 *initializer\-list*:  
 *initializer*  
  
 *initializer\-list*  **,**  *initializer*  
  
 *type\-name*:  
 *specifier\-qualifier\-list abstract\-declarator* opt  
  
 *typedef\-name*:  
 *識別項*  
  
 *extended\-decl\-modifier\-seq*:\/\*    Microsoft 專有 \*\/  
 *extended\-decl\-modifier* opt  
  
 *extended\-decl\-modifier\-seq extended\-decl\-modifier*  
  
 *extended\-decl\-modifier*:   \/\* Microsoft 專有 \*\/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## 請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)   
 [階段結構文法](../c-language/phrase-structure-grammar.md)   
 [過時呼叫慣例](../cpp/obsolete-calling-conventions.md)