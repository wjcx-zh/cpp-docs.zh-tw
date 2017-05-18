---
title: "編譯器警告 （層級 1） C4917 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4917
dev_langs:
- C++
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: 43dce460fb336b09ce39d3e4c0e52b43a175ea36
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4917"></a>編譯器警告 (層級 1) C4917
'declarator': GUID 僅能與類別、 介面或命名空間相關聯  
  
使用者定義的結構以外[類別](../../cpp/class-cpp.md)，[介面](../../cpp/interface.md)，或[命名空間](../../cpp/namespaces-cpp.md)不能有 GUID。  
  
此警告預設為關閉。 請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
下列程式碼範例會產生 C4917:  
  
```cpp  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```
