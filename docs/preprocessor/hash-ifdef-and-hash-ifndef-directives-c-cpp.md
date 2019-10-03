---
title: '#ifdef 和 #ifndef 指示詞 (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 433076388f3646b19d75a907c6b2254098096688
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220111"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 和 #ifndef 指示詞 (CC++/)

當與**已定義**的運算子搭配使用時, **#ifdef**和 **#ifndef**指示詞的效果與[#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)指示詞相同。

## <a name="syntax"></a>語法

> **#ifdef** *識別碼*\
> **#ifndef** *識別碼*

這些指示詞相當於:

> **#if 定義** *識別碼*\
> **#if! 已定義** *識別碼*

## <a name="remarks"></a>備註

您可以使用 **#ifdef**和`#if`可以使用的 **#ifndef**指示詞。 當已定義*識別碼*時, **#ifdef** *identifier*語句就相當於`#if 1` 。 當 identifier 尚未定義`#if 0` ,或已由`#undef`指示詞未定義時, 它就相當於。 這些指示詞只會檢查 `#define` 所定義的識別項是否存在，不適用於 C 或 C++ 原始程式碼中宣告的識別項。

提供這些指示詞的目的只是為了保留與舊版語言的相容性。 偏好搭配指示詞`#if`使用的**已定義 (** *identifier* **)** 常數運算式。

**#Ifndef**指示詞會檢查 **#ifdef**所檢查的條件是否相反。 如果尚未定義識別碼, 或其定義已被移除`#undef`, 則條件為 true (非零)。 否則，條件為 false (0)。

**Microsoft 專屬**

您可以使用[/d](../build/reference/d-preprocessor-definitions.md)選項, 從命令列傳遞*識別碼*。 最多可以使用指定30個`/D`宏。

**#Ifdef**指示詞適用于檢查定義是否存在, 因為可以從命令列傳遞定義。 例如：

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)
