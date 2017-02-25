---
title: "解構函式語意的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "解構函式, C++"
  - "完成項 [C++]"
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 解構函式語意的變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，類別解構函式語意已經大幅變更。  
  
 在 Managed Extensions 中，在參考類別 \(而不是在實值類別\) 內允許類別解構函式。  這在新語法中未變更。  然而，類別解構函式語意已變更。  本主題內容主要在說明變更的原因，並討論它如何影響現有 CLR 程式碼的轉譯。  這可能是此語言兩個版本之間最重要的程式設計人員層級變更。  
  
## 不具決定性最終處理  
 與物件相關的記憶體被記憶體回收行程回收之前，會先叫用相關 `Finalize` 方法 \(如果有的話\)。  您可以把這個方法想像成某種超級解構函式，因為它沒有繫結至物件的程式存留期。  我們稱之為「最終處理」\(finalization\)。  `Finalize` 方法叫用時機或連是否叫用都未定義。  這就是我們說記憶體回收表現不具決定性最終處理的意思。  
  
 不具決定性最終處理可以和動態記憶體管理搭配使用。  當可用記憶體不夠時，記憶體回收行程會介入。  在記憶體回收的環境中，不需要釋放記憶體的解構函式。  當物件持有重要資源，例如資料庫連接或某種鎖定時，不具決定性最終處理便無法正常運作。  這時候，我們應該盡快釋放該資源。  在原生的世界中，這是使用建構函式\/解構函式組來達成。  一旦物件存留期結束 \(當宣告該物件的本機區塊結束時，或因為擲回例外狀況而解開堆疊時\)，解構函式會執行，資源就會自動釋放。  這種作法非常有效，但很可惜 Managed Extensions 中缺少它。  
  
 CLR 所提供的方案是讓類別實作 `IDisposable` 介面的 `Dispose` 方法。  它的問題是，`Dispose` 需要由使用者明確叫用。  這很容易產生錯誤。  C\# 語言以特殊 `using` 陳述式的形式，提供適度的自動化形式。  Managed Extensions 設計不提供特殊支援。  
  
## Managed Extensions for C\+\+ 中的解構函式  
 在 Managed Extensions 中，參考類別的解構函式是使用下列兩個步驟實作：  
  
1.  使用者提供的解構函式在內部被重新命名為 `Finalize`。  如果類別有基底類別 \(請記住，在 CLR 物件模型中只支援單一繼承\)，編譯器在執行使用者提供的程式碼之後，接著會插入呼叫其完成項。  例如，看看從 Managed Extensions 語言規格取得的下列簡單階層架構：  
  
```  
__gc class A {  
public:  
   ~A() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   ~B() { Console::WriteLine(S"in ~B");  }  
};  
```  
  
 在這個範例中，兩個解構函式都重新命名為 `Finalize`。  在 `WriteLine` 引動之後，`B` 的 `Finalize` 會加入 `A` 的 `Finalize` 方法引動。  這是記憶體回收行程在最終處理期間會預設叫用的。  以下是這個內部轉換的相關程式碼：  
  
```  
// internal transformation of destructor under Managed Extensions  
__gc class A {  
public:  
   void Finalize() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   void Finalize() {   
      Console::WriteLine(S"in ~B");  
      A::Finalize();   
   }  
};  
```  
  
1.  在第二個步驟中，編譯器會合成虛擬解構函式。  這個解構函式就是 Managed Extensions 使用者程式直接或間接透過刪除運算式應用所叫用的。  但記憶體回收行程絕不會叫用它。  
  
     這個合成的解構函式中放了兩個陳述式。  一個會呼叫 `GC::SuppressFinalize`，以確定沒有其他 `Finalize` 引動。  第二個會實際引動 `Finalize`，它代表該類別之使用者提供的解構函式。  以下是相關程式碼：  
  
```  
__gc class A {  
public:  
   virtual ~A() {  
      System::GC::SuppressFinalize(this);  
      A::Finalize();  
   }  
};  
  
__gc class B : public A {  
public:  
   virtual ~B() {  
      System::GC::SuppressFinalize(this);  
      B::Finalize();  
   }  
};  
```  
  
 雖然這個實作允許使用者現在 \(而不是您無法控制時\) 明確叫用類別 `Finalize` 方法，但它與 `Dispose` 方法方案並沒有實際結合。  這在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中已經變更。  
  
## 新語法中的解構函式  
 在新語法中，解構函式會在內部被重新命名為 `Dispose` 方法，並且參考類別會自動擴充，以實作 `IDispose` 介面。  也就是說，在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中，我們的類別組已經轉換如下：  
  
```  
// internal transformation of destructor under the new syntax  
__gc class A : IDisposable {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~A");  
   }  
};  
  
__gc class B : public A {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~B");    
      A::Dispose();   
   }  
};  
```  
  
 在新語法中叫用解構函式，或當 `delete` 套用至追蹤控制代碼時，會自動叫用基礎 `Dispose` 方法。  如果它是衍生類別，會在合成方法結尾插入基底類別的 `Dispose` 方法呼叫。  
  
 但這不能讓我們直達具決定性的最終處理。  若要達成此目標，我們需要本機參考物件的額外支援 \(在 Managed Extensions 中沒有類似支援，所以不構成轉換問題\)。  
  
## 宣告參考物件  
 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 支援在本機堆疊上參考類別之物件的宣告，或將物件視為可直接存取之類別的成員方式宣告。  結合解構函式與 `Dispose` 方法的關聯時，結果是在參考型別上最終處理語意的自動引動。  
  
 首先，我們會定義參考類別，讓物件建立的作用如同透過其類別建構函式的資源擷取。  其次，在類別解構函式內，當物件已建立時，我們會釋放所需的資源。  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // … everything else …  
};  
```  
  
 使用型別名稱 \(但不含伴隨的帽子\) 在本機宣告物件。  所有物件的使用 \(例如叫用方法\) 都是透過成員選取點 \(`.`\) 而不是箭號 \(`->`\) 完成。  在區塊結尾，會自動叫用已轉換成 `Dispose` 的相關聯解構函式，如此處所示：  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here –  
   // that is, r.Dispose() is invoked  
}  
```  
  
 如同 C\# 中的 `using` 陳述式，這並未違反所有參考型別都必須配置在 CLR 堆積上的基礎 CLR 限制。  基礎語意維持不變。  使用者可能已撰寫下列對等程式碼 \(而且這可能是由編譯器所執行的內部轉換\)：  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 在新語法中，解構函式實際上再次與建構函式搭檔，做為繫結至本機物件存留期的自動化擷取\/釋放機制。  
  
## 宣告明確 Finalize  
 在新語法中，如我們所見，解構函式會合成為 `Dispose` 方法。  這表示，當解構函式未明確叫用時，記憶體回收行程在最終處理期間不會像以前一樣尋找物件相關聯的 `Finalize` 方法。  為了支援解構和最終化，我們引進了特殊語法來提供完成項。  例如：  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!` 前置字元類似引入類別解構函式的波狀符號 \(`~`\)，也就是說，兩個存留期後方法在類別名稱前都有前置語彙基元。  如果合成 `Finalize` 方法在衍生類別內發生，基底類別 `Finalize` 方法的引動會在其結尾插入。  如果解構函式是明確叫用，則會隱藏完成項。  以下是轉換的相關程式碼：  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## 從 Managed Extensions for C\+\+ 移至 Visual C\+\+ 2010  
 當 Managed Extensions for C\+\+ 程式在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 當中編譯，而參考類別包含非一般的解構函式時，其執行階段行為已變更。  必要的轉換演算法類似下列方式：  
  
1.  如果解構函式存在，將它重寫成類別完成項。  
  
2.  如果 `Dispose` 方法存在，將它重寫成類別解構函式。  
  
3.  如果解構函式存在，但沒有 `Dispose` 方法，則保留解構函式，同時執行第一個項目。  
  
 當您將程式碼從 Managed Extensions 移至新語法時，您可能會遺漏執行此轉換。  如果應用程式在某些方面相依於相關最終處理方法的執行，則應用程式行為將不符您的預期，而且不會出現訊息。  
  
## 請參閱  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Visual C\+\+ 中的解構函式和完成項](../misc/destructors-and-finalizers-in-visual-cpp.md)