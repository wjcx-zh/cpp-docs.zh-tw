---
title: "Overview of Generics in Visual C++ | Microsoft Docs"
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
  - "generics [C++], about generics"
  - "default initializers [C++]"
  - "type parameters [C++]"
  - "constructed types"
  - "type arguments [C++]"
  - "constructed types, open [C++]"
  - "open constructed types [C++]"
  - "constructed types, closed [C++]"
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Overview of Generics in Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型是 Common Language Runtime 支援的參數化型別。  如果使用的是泛型，參數化型別是定義為未知的型別參數指定的型別。  
  
## 為何泛型？  
 C\+\+ 支援樣板且樣板和泛型皆支援參數化型別建立型別的集合類別。  不過，範本提供編譯時期參數化。  您無法參考包含樣板定義的組件並建立範本的新特製化。  一旦編譯，特定範本看起來與其他類別或方法相似。  相反地，泛型在 MSIL 發出做為執行階段已知參數化型別是參數化型別；參考包含泛型型別之組件的原始程式碼可以建立泛型類別的特製化。  如需 Visual C\+\+ 樣板和泛型的詳細比較，請參閱 [Generics and Templates \(Visual C\+\+\)](../windows/generics-and-templates-visual-cpp.md)。  
  
## 泛型函式和型別  
 類別的型別，只要是 Managed 型別，就可能是泛型。  這樣的範例可以是 `List` 類別。  清單中的物件的型別會是型別參數。  如果您需要物件的許多不同類型的 `List` 類別，在這種情況下，在泛型之前，您可能已經使用採用**System::Object** 作為項目型別的 `List`。  但是，這會允許所有物件 \(包括錯誤型別的物件\) 用於清單。  這類清單將呼叫不具型別集合類別。  最佳的情況是，您可以在執行階段檢查這個型別，且擲回例外狀況。  或者，您可能使用了樣板，將會失去其普通品質一次編譯成組件。  您組件的消費者無法建立項目範本的特製化。  泛型可讓您建立具型別集合類別，例如 `List<int>` \(讀為"List of int"\) 及  `List<double>` \(讀為"List of double"\)，如果您嘗試將非設計成接受的集合之型別放入型別集合中，它們將會產生編譯時期錯誤。  此外，這些型別在編譯之後仍然是泛型。  
  
 泛型類別語法的說明在 [Generic Classes \(C\+\+\/CLI\)](../windows/generic-classes-cpp-cli.md)`.` 的新命名空間， <xref:System.Collections.Generic> 可能會找到，引入一組參數化的集合型別包括 <xref:System.Collections.Generic.Dictionary%602>、 <xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.LinkedList%601>。  如需詳細資訊，請參閱[.NET Framework 類別庫中的泛型](../Topic/Generics%20in%20the%20.NET%20Framework%20Class%20Library%20\(C%23%20Programming%20Guide\).md)。  
  
 執行個體和靜態類別成員函式、委派及全域函式也可以是泛型。  若函式的參數是未知的型別，或者如果函式必須與泛型型別一起使用，泛型函式可能是必要的。  在大部分情況下 **System::Object** 可能用來做為參數為未知的物件型別的地方，可以由泛型型別參數替代，允許更多的型別安全程式碼。  任何嘗試在非函式所設計的型別中傳遞將會在編譯時期標記為錯誤。  使用 **System::Object** 為函式參數，函式不適合處理的物件的無效傳遞將不會被偵測到，您必須將未知的物件型別轉型為函式主體中特定的型別，並負責 InvalidCastException 的可能性。  具有泛型，嘗試傳遞物件至函式的程式碼將會引起型別衝突，因此函式主體保證具有正確的型別。  
  
 相同的優點適用於泛型集合中建立的類別。  過去的集合類別將使用 **System::Object** 儲存項目至集合中。  型別的物件插入集合不是設計為未旗標在編譯時期，而且通常不是，即使已插入物件。  通常，當物件在集合中存取，他將會轉換成其他型別。  只有在轉換失敗時會偵測到未預期的型別。  泛型在編譯時期藉由偵測插入型別不符合的所有程式碼 \(或隱含轉換\) 泛型集合的型別參數來解決這個問題。  
  
 如需語法的說明，請參閱 [Generic Functions \(C\+\+\/CLI\)](../windows/generic-functions-cpp-cli.md)。  
  
## 詞彙使用泛型  
  
##### 型別參數  
 泛型宣告含有一或多個未知的型別，稱為 *型別參數*。  型別參數會被給予代表泛型宣告主體中的型別之名稱。  型別參數作為代表泛型宣告主體中的型別使用。  List\<T\> 的泛型宣告包含型別參數 T。  
  
##### 型別引數  
 表示泛用為特定型別或型別時，*型別引數* 是型別使用的實體型別參數位置。  例如， `int` 是在 `List<int>` 中的型別引數。  實值型別和控制代碼型別是泛型型別引數所允許的型別。  
  
##### 建構的型別  
 從泛型型別建構的型別的型別被稱為 *constructed type*。  型別不完整指定，例如 `List<T>` 為開放式建構 *型別*；型別完整指定，例如 `List<double>,` 為 *封閉式建構型別* 或 *特定型別*。  開放式建構型別可用於其他泛型型別或方法的定義，不可以完整指定，直到封入泛型本身指定。  例如，下列是開放式建構型別當做泛型基底類別：  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### 條件約束  
 條件約束是可做為型別參數的型別的限制。  例如，指定泛型類別可以接受從指定的類別繼承的類別，或者實作指定的介面。  如需詳細資訊，請參閱[Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 參考型別和實質型別  
 控制代碼型別和實值型別可以使用做為型別引數。  在泛型定義，任一個型別可以使用，語法是參考型別。  例如， **\-\>** 運算子來存取型別參數之型別的成員，無論最終使用的型別是參考型別或實值型別。  當實值型別當做實值型別直接使用，而不需對實值型別進行 Box 的型別引數時，執行階段會產生程式碼。  
  
 當使用參考型別做為泛型型別引數時，請使用控制代碼語法。  當使用實值型別做為泛型型別引數時，請直接使用這個型別的名稱。  
  
 `// generics_overview_2.cpp`  
  
 `// compile with: /clr`  
  
 `generic <typename T>`  
  
 `ref class GenericType {};`  
  
 `ref class ReferenceType {};`  
  
 `value struct ValueType {};`  
  
 `int main() {`  
  
 `GenericType<ReferenceType^> x;`  
  
 `GenericType<ValueType> y;`  
  
 `}`  
  
## 型別參數  
 在泛型類別的型別參數視為其他識別項。  不過，因為型別未知，因此限制其用途。  例如，您不能使用成員及這個型別參數的方法，除非型別參數知道支援這些成員。  透過型別參數存取成員，您必須將包含成員的型別加入至型別參數的條件約束清單。  
  
 `// generics_overview_3.cpp`  
  
 `// compile with: /clr`  
  
```  
interface class I {  
   void f1();  
   void f2();  
};  
  
ref struct R : public I {  
   virtual void f1() {}  
   virtual void f2() {}   
   virtual void f3() {}   
};  
  
generic <typename T>  
where T : I  
void f(T t) {  
   t->f1();  
   t->f2();  
   safe_cast<R^>(t)->f3();  
}  
  
int main() {  
   f(gcnew R());  
}  
```  
  
 這些限制也適用於運算子。  以免型別不支援這些運算子，不受限制的泛型型別參數不能使用 `==` 和 `!=` 運算子比較這個型別參數的兩個執行個體。  為泛型這些檢查是必要的，但不可為樣板，因為在無法檢查使用無效的成員時，泛型可能是專門用來以滿足條件約束的任何類別的執行階段。  
  
 可能使用 `()` 運算子，建立型別參數的預設執行個體。  例如：  
  
 `T t = T();`  
  
 其中 `T` 是一個泛型類別或方法定義中的型別參數，初始化變數為其預設值。  如果 `T` 是 ref 類別，它會是 null 指標；如果 `T` 是實值類別，則物件會初始化為零。  這個稱為 *預設初始設定式*。  
  
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)