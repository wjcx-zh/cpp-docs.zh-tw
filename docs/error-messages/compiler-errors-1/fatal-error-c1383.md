---
title: 嚴重錯誤 C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 6c0be830cb56b760f1397ea2b2f81b42a87e9ba6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203082"
---
# <a name="fatal-error-c1383"></a>嚴重錯誤 C1383

編譯器選項 /GL 與所安裝 Common Language Runtime 的版本不相容

搭配使用舊版的 Common Language Runtime 與較新的編譯器時，以及使用 **/clr** 和 **/GL.** 編譯時，會發生 C1383。

若要解決，請不要搭配使用 **/GL** 與 **/clr** ，或安裝編譯器所隨附的 Common Language Runtime 版本。

如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 與 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。
