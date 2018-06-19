---
title: 編譯器錯誤 C3201 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3201
dev_langs:
- C++
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51ebf253a1d1e5963ff05aa343295e133a0641c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254995"
---
# <a name="compiler-error-c3201"></a>編譯器錯誤 C3201
類別範本 'template' 的樣板參數清單不符合範本參數 'template' 的範本參數清單  
  
 您將引數中的類別範本傳遞至不接受範本參數的類別範本，或是為預設範本引數傳遞了數目不符的範本引數。  
  
```  
// C3201.cpp  
template<typename T1, typename T2>  
class X1  
{  
};  
  
template<template<typename T> class U = X1>   // C3201  
class X2  
{  
};  
  
template<template<typename T, typename V> class U = X1>   // OK  
class X3  
{  
};  
```