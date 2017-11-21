---
title: "編譯器錯誤 C2788 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2788
dev_langs: C++
helpviewer_keywords: C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3d66496da2940a08d87f968678125b5836587ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2788"></a>編譯器錯誤 C2788
'identifier': 與此物件相關聯的一個以上的 GUID  
  
 [__Uuidof](../../cpp/uuidof-operator.md)運算子採用的使用者定義型別與附加的 GUID 或這類使用者定義型別的物件。 當引數是具有多個 Guid 的物件時，就會發生此錯誤。  
  
 下列範例會產生 C2788:  
  
```  
// C2788.cpp  
#include <windows.h>  
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};  
template <class T, class U> class MyClass {};  
  
typedef MyClass<A,B> MyBadClass;  
typedef MyClass<A,A> MyGoodClass;  
  
int main() {  
   __uuidof(MyBadClass);    // C2788  
   // try the following line instead  
   __uuidof(MyGoodClass);  
}  
```