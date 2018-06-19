---
title: 編譯器警告 （層級 1） C4917 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4917
dev_langs:
- C++
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afc38da9bb06879745fb96afd8224a4f599bb252
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298859"
---
# <a name="compiler-warning-level-1-c4917"></a>編譯器警告 (層級 1) C4917
'declarator': GUID 僅能與類別、 介面或命名空間相關聯  
  
使用者定義的結構以外[類別](../../cpp/class-cpp.md)，[介面](../../cpp/interface.md)，或[命名空間](../../cpp/namespaces-cpp.md)不能有 GUID。  
  
此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
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