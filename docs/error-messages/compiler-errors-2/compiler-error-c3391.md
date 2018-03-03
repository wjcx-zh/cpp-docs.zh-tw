---
title: "編譯器錯誤 C3391 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3391
dev_langs:
- C++
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5302939fa8a77a244c039d45c10ea5596897240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3391"></a>編譯器錯誤 C3391
'type_arg': 對泛型參數 'param' 屬於泛型 'generic_type'，不正確的型別引數必須是不可為 null 的實值型別  
  
泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱<xref:System.Nullable>和[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
下列範例會使用 C#，建立包含具有 C + 中撰寫泛型類型時，不支援的特定條件約束的泛型類型的元件 + CLI。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
```cs  
// C3391.cs  
// Compile by using: csc /target:library C3391.cs  
// a C# program  
public class GR<N>  
where N : struct {}  
```  
  
可用 C3391.dll 元件時，下列範例會產生 C3391。  
  
```cpp  
// C3391_b.cpp  
// Compile by using: cl /clr C3391_b.cpp  
#using <C3391.dll>  
using namespace System;  
value class VClass {};  
  
int main() {  
   GR< Nullable<VClass> >^ a =   
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable  
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK  
}  
```