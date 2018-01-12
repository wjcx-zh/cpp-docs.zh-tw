---
title: "編譯器錯誤 C2429 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2429
dev_langs: C++
helpviewer_keywords: C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6882804d1ddf2e4f83947e310cde4c8c114120d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2429"></a>編譯器錯誤 C2429

> '*語言功能*'需要編譯器旗標'*編譯器選項*'

語言功能需要支援特定的編譯器選項。

錯誤**C2429： 語言功能 '巢狀命名空間-定義' 需要編譯器旗標 ' / std:c + + 17'**如果您嘗試定義就會產生*複合命名空間*，包含一個以上的命名空間從 Visual Studio 2015 Update 5 的範圍巢狀命名空間名稱。 (在 Visual Studio 2017 版本 15.3， **/std:c + + 最新**參數是必要。)複合定義中不允許使用 c + + 在 C + + 17 之前的命名空間。 編譯器支援複合的命名空間定義當[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)編譯器選項指定：

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
