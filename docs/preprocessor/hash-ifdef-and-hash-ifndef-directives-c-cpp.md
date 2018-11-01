---
title: '#ifdef 和 #ifndef 指示詞 （C/c + +）'
ms.date: 11/04/2016
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 418b19e844d56fa2f33cf91a1b072e9add771eb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643790"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 和 #ifndef 指示詞 (C/C++)
**#Ifdef**並 **#ifndef**指示詞會執行相同的工作`#if`指示詞搭配使用時**定義**(*識別碼* ).

## <a name="syntax"></a>語法

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>備註

您可以使用 **#ifdef**並 **#ifndef**任何位置的指示詞`#if`可用。 **#Ifdef** *識別項*陳述式相當於`#if 1`時*識別碼*已定義，而且它相當於`#if 0`時*識別碼*未定義或取消定義與`#undef`指示詞。 這些指示詞只會檢查 `#define` 所定義的識別項是否存在，不適用於 C 或 C++ 原始程式碼中宣告的識別項。

提供這些指示詞的目的只是為了保留與舊版語言的相容性。 **定義 (** *識別項* **)** 搭配使用的常數運算式`#if`最好使用指示詞。

**#Ifndef**指示詞會檢查所檢查的條件相反 **#ifdef**。 如果尚未定義識別項 (或是已使用 `#undef` 移除其定義)，則條件為 true (非零)。 否則，條件為 false (0)。

**Microsoft 專屬**

*識別碼*可以從命令列使用傳遞`/D`選項。 您可以使用指定最多 30 個巨集`/D`。

這個選項在檢查定義是否存在時很實用，因為可以從命令列傳遞定義。 例如: 

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)