---
title: "Constraints on Generic Type Parameters (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "where"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "where keyword [C++]"
  - "constraints, C++"
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
caps.latest.revision: 25
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Constraints on Generic Type Parameters (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在泛型型別或方法宣告，您可以加上條件約束的型別參數。  條件約束是型別使用的要求，型別引數必須滿足。  例如，條件約束會是型別引數必須實作特定介面或從特定類別繼承。  
  
 條件約束是選擇性的；未指定條件約束在參數與限制該參數相當於 <xref:System.Object>。  
  
## 語法  
  
```  
  
where type-parameter: constraint list  
```  
  
#### 參數  
 *型別參數*  
 一個型別參數，要限制。  
  
 *條件約束清單*  
 *條件約束清單* 是條件約束規格的逗號分隔清單。  清單可以包含這個型別實作介面的參數。  
  
 清單也可以包括類別。  對於這個型別符合基底類別條件約束的引數，它必須是相同的類別條件約束或從條件約束衍生。  
  
 您也可以指定 `gcnew()` 表示型別引數必須有公用的無參數建構函式：或者表示型別的 `ref class` 引數必須是參考型別，包括任何類別、介面、委派或陣列型別;或者表示型別的 `value class` 引數必須是實值型別。  您可以指定空的 \<T\> 以外的任何實值型別。  
  
 您也可以指定泛型參數做為條件約束。  這個型別為您限制的型別提供的引數必須是或從條件約束的型別衍生。  這稱為 Naked 型別條件約束。  
  
## 備註  
 條件約束子句包含型別的參數，冒號 \(**:**\) 和條件式後面接著 **where** ，在型別參數中指定這個限制的性質。  **where** 為內容相關性關鍵字。如需詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  以空格分隔多個 **where** 子句。  
  
 條件約束套用至型別參數加入至可當做引數為泛型型別或方法之型別的限制。  
  
 類別和介面條件約束指定引數型別必須是或衍生自指定的類別繼承或實作特定的介面。  
  
 條件約束的應用程式對泛型型別或方法的允許該型別或方法的程式碼使用條件約束型別的已知的功能。  例如，您可以宣告泛型類別 ，其中指定由型別參數來實作 **IComparable\<T\>**：  
  
```  
// generics_constraints_1.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : IComparable<T>  
ref class List {};  
```  
  
 這個條件約束要求在編譯時期型別用於 `T` 的引數實作 `IComparable<T>`。  它也允許介面方法來呼叫，例如 **CompareTo**。  轉換不需要在型別參數中的執行個體呼叫介面方法。  
  
 在型別引數之類別的靜態方法無法透過型別參數呼叫；它們只可以被實際具名型別呼叫。  
  
 條件約束不能是實值型別，包括內建型別 \(例如 `int` 或 **double**。  因為實值型別不能有衍生類別，只有一個類別可以滿足條件約束。  在這種情況下，泛型可以覆寫與型別特定實值型別取代參數。  
  
 在某些情況下需要條件約束，因為編譯器不允許使用方法或未知型別的其他功能，除非條件約束表示未知的型別支援方法或介面。  
  
 同一個型別參數的條件約束會以逗號分隔的清單中加以指定。  
  
```  
// generics_constraints_2.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
generic <typename T>  
where T : List<T>, IComparable<T>  
ref class List {};  
```  
  
 如果是多重型別參數，則每個型別參數都要有一個 **where** 子句  例如：  
  
```  
// generics_constraints_3.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <typename K, typename V>  
   where K: IComparable<K>  
   where V: IComparable<K>  
ref class Dictionary {};  
```  
  
 總之，在程式碼使用條件約束會根據下列規則:  
  
-   如果多個條件約束清單，條件約束可以任何順序列出。  
  
-   條件約束也是類別型別，例如抽象基底類別。  不過，條件約束不可以是實值型別或密封類別。  
  
-   條件約束本身不能是型別參數，但是，在開放式建構型別可以包含型別參數。  例如：  
  
    ```  
    // generics_constraints_4.cpp  
    // compile with: /c /clr  
    generic <typename T>  
    ref class G1 {};  
  
    generic <typename Type1, typename Type2>  
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter  
    ref class G2{};  
    ```  
  
## 範例  
 下列範例會在呼叫型別參數的執行個體方法中使用條件約束。  
  
```  
// generics_constraints_5.cpp  
// compile with: /clr  
using namespace System;  
  
interface class IAge {  
   int Age();  
};  
  
ref class MyClass {  
public:  
   generic <class ItemType> where ItemType : IAge   
   bool isSenior(ItemType item) {  
      // Because of the constraint,  
      // the Age method can be called on ItemType.  
      if (item->Age() >= 65)   
         return true;  
      else  
         return false;  
   }  
};  
  
ref class Senior : IAge {  
public:  
   virtual int Age() {  
      return 70;  
   }  
};  
  
ref class Adult: IAge {  
public:  
   virtual int Age() {  
      return 30;  
   }  
};  
  
int main() {  
   MyClass^ ageGuess = gcnew MyClass();  
   Adult^ parent = gcnew Adult();  
   Senior^ grandfather = gcnew Senior();  
  
   if (ageGuess->isSenior<Adult^>(parent))  
      Console::WriteLine("\"parent\" is a senior");  
   else  
      Console::WriteLine("\"parent\" is not a senior");  
  
   if (ageGuess->isSenior<Senior^>(grandfather))  
      Console::WriteLine("\"grandfather\" is a senior");  
   else  
      Console::WriteLine("\"grandfather\" is not a senior");  
}  
```  
  
  **"parent" is not a senior**  
**"grandfather" is a senior**   
## 範例  
 當泛型型別參數當做條件約束時，稱為 Naked 型別條件約束。  表示與其型別參數的 10% 成員函式需要限制該參數至包含型別時，型別參數 Naked 型別條件約束就很有用。  
  
 在下列範例中， T 是加入方法內容中 Naked 型別條件約束。  
  
 Naked 型別參數也可以在泛型類別定義中使用。  做為 Naked 型別條件約束對泛型類別來說不會有用，因為編譯器除了只能將 Naked 型別約束條件視為是衍生自 <xref:System.Object> 之外，無法做任何假設。  如果您要強制兩型別參數之間的繼承關係時，請在泛型類別上使用 Naked 型別條件約束。  
  
```  
// generics_constraints_6.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct List {  
   generic <class U>  
   where U : T  
   void Add(List<U> items)  {}  
};  
  
generic <class A, class B, class C>  
where A : C  
ref struct SampleClass {};  
```  
  
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)