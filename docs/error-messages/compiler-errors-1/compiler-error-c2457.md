---
title: "編譯器錯誤 C2457 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2457
dev_langs:
- C++
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff89bb3635936ae0f797438d73f71adf1ef08de7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2457"></a>編譯器錯誤 C2457

> '*巨集*': 預先定義巨集不能出現在函式主體之外

您嘗試使用預先定義的巨集，例如[&#95; &#95;函式 &#95; &#95;](../../preprocessor/predefined-macros.md)，全域空間中。

## <a name="example"></a>範例

下列範例會產生 C2457，並也會顯示正確的使用方式：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```