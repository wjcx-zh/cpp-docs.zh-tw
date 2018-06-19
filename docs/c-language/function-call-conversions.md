---
title: 函式呼叫轉換 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71b0fc4468ea98f04c87c8389021f2e12d9cae69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384492"
---
# <a name="function-call-conversions"></a>函式呼叫轉換
在函式呼叫的引數上執行的類型轉換取決於函式原型 (向前宣告) 是否存在，以及所呼叫之函式宣告的引數類型。  
  
 如果函式原型存在並且包含宣告的引數類型，則編譯器會執行類型檢查 (請參閱[函式](../c-language/functions-c.md))。  
  
 如果函式原型不存在，則只會在函式呼叫中的引數上執行一般算術轉換。 這些轉換會單獨在呼叫中的各個引數上執行。 這表示 **float** 值會轉換成 **double**；`char` 或 **short** 值會轉換為 `int`；而 `unsigned char` 或 **unsigned short** 會轉換為 `unsigned int`。  
  
## <a name="see-also"></a>請參閱  
 [類型轉換](../c-language/type-conversions-c.md)