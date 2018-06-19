---
title: 編譯器錯誤 C2947 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2947
dev_langs:
- C++
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1af4e6a5a27c13d69351eaf0cddfafe11ba5f22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243427"
---
# <a name="compiler-error-c2947"></a>編譯器錯誤 C2947
必須以 '>' 結束 construct，但卻找到 'syntax'  
  
 使用泛型或樣板引數清單可能不正確地終止。  
  
 C2947 也可能會產生語法錯誤。  
  
 下列範例會產生 C2947:  
  
```  
// C2947.cpp  
// compile with: /c  
template <typename T>=   // C2947  
// try the following line instead  
// template <typename T>  
struct A {};  
```