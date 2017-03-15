---
title: "編譯器錯誤 C3391 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3391
dev_langs:
- C++
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: 7b5922ccf353162dc32c99e3818227639d0f5985
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3391"></a>編譯器錯誤 C3391
'type_arg': 無效的型別引數的泛型參數的泛型 'generic_type'，' 參數必須是不可為 null 的實值型別  
  
泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱<xref:System.Nullable>和[泛型](../../windows/generics-cpp-component-extensions.md)。</xref:System.Nullable>  
  
## <a name="example"></a>範例  
下列範例會使用 C# 建立元件，其中包含已撰寫 C + 中的泛型型別時，不支援某些條件約束的泛型型別 + CLI。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/articles/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
```cs  
// C3391.cs  
// Compile by using: csc /target:library C3391.cs  
// a C# program  
public class GR<N>  
where N : struct {}  
```  
  
C3391.dll 元件可用時，下列範例會產生 C3391。  
  
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
