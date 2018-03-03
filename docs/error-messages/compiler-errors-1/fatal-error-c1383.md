---
title: "嚴重錯誤 C1383 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24e9d7652c96c84f94bafbf2c808f2e5430037b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1383"></a>嚴重錯誤 C1383
編譯器選項 /GL 與所安裝 Common Language Runtime 的版本不相容  
  
 搭配使用舊版的 Common Language Runtime 與較新的編譯器時，以及使用 **/clr** 和 **/GL.**編譯時，會發生 C1383。  
  
 若要解決，請不要搭配使用 **/GL** 與 **/clr** ，或安裝編譯器所隨附的 Common Language Runtime 版本。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 與 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。