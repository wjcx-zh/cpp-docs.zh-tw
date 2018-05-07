---
title: 編譯器錯誤 C2756 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2756
dev_langs:
- C++
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3eb61cd111166867be0439709a8b73dd4056099
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2756"></a>編譯器錯誤 C2756
'template type'：在部分特製化上不允許預設的範本引數  
  
 部分特製化的範本不能包含預設引數。  
  
 下列範例會產生 C2756，並示範如何修正此問題：  
  
```  
// C2756.cpp  
template <class T>  
struct S {};  
  
template <class T=int>  
// try the following line instead  
// template <class T>  
struct S<T*> {};   // C2756  
```