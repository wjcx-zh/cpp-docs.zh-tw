---
title: "編譯器錯誤 C3268 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3268
dev_langs:
- C++
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c31177aa65d3a16b85e9089c6f740e2106c6fe6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3268"></a>編譯器錯誤 C3268
'function': 泛型類別的泛型函式或成員函式不能有變數參數清單  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 請參閱[泛型](../../windows/generics-cpp-component-extensions.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3268。  
  
```  
// C3268.cpp  
// compile with: /clr:pure /c  
generic <class ItemType>  
void Test(ItemType item, ...) {}   // C3268  
// try the following line instead  
// void Test(ItemType item) {}  
  
generic <class ItemType2>  
ref struct MyStruct { void Test(...){} };   // C3268  
// try the following line instead  
// ref struct MyStruct { void Test2(){} };   // OK  
```