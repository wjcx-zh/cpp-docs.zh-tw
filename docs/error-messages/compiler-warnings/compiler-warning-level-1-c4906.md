---
title: "編譯器警告 （層級 1） C4906 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4906
dev_langs:
- C++
helpviewer_keywords:
- C4906
ms.assetid: 05318e74-799b-412a-9dce-f02b8161d762
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba4ce917a0ed9b4c900ba39f5ab2d84f02ca44be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4906"></a>編譯器警告 (層級 1) C4906
字串常值轉換成 'LPWSTR'  
  
 編譯器偵測到不安全的轉換。 轉換未成功，但您應該使用的轉換常式。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4906:  
  
```  
// C4906.cpp  
// compile with: /W1  
#pragma warning(default : 4906)  
#include <windows.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
    LPWSTR x = (LPWSTR)"1234";   // C4906  
  
    // try the following lines instead  
    // char y[128];  
    // size_t numberOfCharConverted = 0;  
    // errcode err = 0;  
    // err = wcstombs_s(&numberOfCharConverted , &y[0], 128,  
    //                  L"12345", 4);  
    // if (err != 0)  
    // {  
    //     printf_s("wcstombs_s failed!");  
    //     return -1;  
    // }  
    // printf_s("%s\n", y);  
  
    return 0;  
}  
```