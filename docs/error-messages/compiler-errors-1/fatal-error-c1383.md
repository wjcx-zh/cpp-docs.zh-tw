---
title: 嚴重錯誤 C1383 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae5e16959597e16f25320778be4d4b45ca5950e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226970"
---
# <a name="fatal-error-c1383"></a>嚴重錯誤 C1383
編譯器選項 /GL 與所安裝 Common Language Runtime 的版本不相容  
  
 搭配使用舊版的 Common Language Runtime 與較新的編譯器時，以及使用 **/clr** 和 **/GL.** 編譯時，會發生 C1383。  
  
 若要解決，請不要搭配使用 **/GL** 與 **/clr** ，或安裝編譯器所隨附的 Common Language Runtime 版本。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 與 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。