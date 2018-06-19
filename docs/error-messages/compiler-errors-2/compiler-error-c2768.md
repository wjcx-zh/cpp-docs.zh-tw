---
title: 編譯器錯誤 C2768 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233379"
---
# <a name="compiler-error-c2768"></a>編譯器錯誤 C2768
'function': 不合法使用明確樣板引數  
  
 編譯器無法判斷是否應該函式定義的函式樣板的明確特製化，或者應該是新的函式的函式定義。  
  
 這個錯誤是在 Visual Studio.NET 2003 中，引進，做為編譯器一致性增強功能的一部分。  
  
 下列範例會產生 C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```