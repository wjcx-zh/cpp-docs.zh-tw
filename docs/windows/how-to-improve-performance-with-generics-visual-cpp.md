---
title: "How to: Improve Performance with Generics (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "performance, C++"
  - "Visual C++, performance"
  - "Visual C++, generics"
  - "generics [C++], performance"
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Improve Performance with Generics (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有了泛型，您也可以根據型別參數建立可重複使用的程式碼。  型別參數的實際型別會由用戶端程式碼延後。  如需泛型的詳細資訊，請參閱 [Generics](../windows/generics-cpp-component-extensions.md)。  
  
 本文將討論泛型如何協助將使用設定應用程式的效能。  
  
## 範例  
 .NET Framework 隨附之 <xref:System.Collections?displayProperty=fullName> 命名空間中的許多集合類別。  大部分集合適用於型別的 <xref:System.Object?displayProperty=fullName>物件。  這可讓集合來儲存任何型別，從任何型別的 .NET Framework，甚至是實值型別，從 <xref:System.Object?displayProperty=fullName>取得。  然而，對這個方法有兩個缺點。  
  
 首先，如果集合儲存實值型別，例如整數，必須在將 Boxed 值加入至集合之前和 Unboxed，當某個值從集合中擷取。  這些是昂貴的作業。  
  
 其次，無法將輸入的控制項可以加入至集合。  它會將整數和字串放在完全合法的同一個集合，因此，即使這可能不是您想要的目的。  因此，您的程式碼可以為型別安全，您必須檢查從集合擷取的型別實際上就是必要的。  
  
 下列程式碼範例說明在泛型之前的 .NET Framework 集合的兩個主要缺點。  
  
```  
// perf_pre_generics.cpp  
// compile with: /clr  
  
using namespace System;  
using namespace System::Collections;  
  
int main()  
{  
    // This Stack can contain any type.  
    Stack ^s = gcnew Stack();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
  
    // Push a String to the same Stack.  
    // The Stack now contains two different data types.  
    s->Push("Seven");  
  
    // Pop the items off the Stack.  
    // The item is returned as an Object, so a cast is  
    // necessary to convert it to its proper type.  
    while (s->Count > 0)  
    {  
        Object ^o = s->Pop();  
        if (o->GetType() == Type::GetType("System.String"))  
        {  
            Console::WriteLine("Popped a String: {0}", (String ^)o);  
        }  
        else if (o->GetType() == Type::GetType("System.Int32"))  
        {  
            Console::WriteLine("Popped an int: {0}", (int)o);  
        }  
        else  
        {  
            Console::WriteLine("Popped an unknown type!");  
        }  
    }  
}  
```  
  
  **Popped a String: Seven**  
**Popped an int: 7**   
## 範例  
 新的 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間包含 <xref:System.Collections?displayProperty=fullName> 命名空間中的許多相同的集合，不過，修改它們接受泛型型別參數。  這會排除非泛型集合兩個缺點: 實值型別 Boxing 和 Unboxing 和不可以指定集合中將儲存的型別。  在兩個集合的作業相同；這些屬性只不同於執行個體化。  
  
 以上寫入的這個範例使用泛型 <xref:System.Collections.Generic.Stack%601> 集合的範例比較。  對於經常存取的大型集合，這個範例將效能明顯大於前一個範例。  
  
```  
// perf_post_generics.cpp  
// compile with: /clr  
  
#using <System.dll>  
  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main()  
{  
    // This Stack can only contain integers.  
    Stack<int> ^s = gcnew Stack<int>();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
    s->Push(14);  
  
    // You can no longer push a String to the same Stack.  
    // This will result in compile time error C2664.  
    //s->Push("Seven");  
  
    // Pop an item off the Stack.  
    // The item is returned as the type of the collection, so no  
    // casting is necessary and no unboxing is performed for  
    // value types.  
    int i = s->Pop();  
    Console::WriteLine(i);  
  
    // You can no longer retrieve a String from the Stack.  
    // This will result in compile time error C2440.  
    //String ^str = s->Pop();  
}  
```  
  
  **14**   
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)