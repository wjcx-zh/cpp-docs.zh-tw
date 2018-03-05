---
title: "解構函式語意變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85ac0b082e8ea1dfbff007a68061e6a286390cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-destructor-semantics"></a>解構函式語意的變更
類別解構函式的語意已大幅變更從 Managed Extensions for c + + Visual c + +。  
  
 在 Managed Extensions，參考類別內，但不是在實值類別允許類別解構函式。 這個新語法中並未變更。 不過，已變更類別的解構函式的語意。 本主題著重在變更的原因，並討論如何影響現有的 CLR 程式碼中的轉譯。 它可能是最重要的程式設計人員層級變更之間的兩個語言版本。  
  
## <a name="non-deterministic-finalization"></a>不具決定性最終處理  
 與物件相關聯的記憶體回收的記憶體回收行程，相關聯之前`Finalize`，如果有的話，會叫用方法。 您可以將這個方法視為一種超級解構函式因為它未繫結至程式物件的存留期。 我們將這稱為最終處理。 執行時間只是當或甚至是否`Finalize`叫用方法未定義。 這也就是我們說回收表現不具決定性最終處理。  
  
 不具決定性最終處理很適合的動態記憶體管理。 當可用記憶體不足時，記憶體回收行程會介入。 環境中，在記憶體回收是沒有必要的解構函式，以釋放記憶體的收集。 不具決定性最終處理不會無法正常運作，不過，當物件會維護重要的資源，例如資料庫連接或某種類型的鎖定。 在此情況下，我們應該儘速釋放該資源。 在原生世界中，以建構函式/解構函式組達成的。 物件存留期結束，因為其宣告所在的本機區塊結束時，或解開堆疊時擲回的例外狀況，因為執行解構函式，就會自動釋放資源。 這種方法非常適合，和真錯過它在 Managed Extensions 並不存在。  
  
 CLR 所提供的解決方案是讓類別來實作`Dispose`方法`IDisposable`介面。 此處的問題在於`Dispose`需要使用者的明確引動過程。 這是容易發生錯誤。 C# 語言形式，提供適度的特殊形式的自動化`using`陳述式。 Managed Extensions 設計會提供任何特殊支援。  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Managed Extensions for c + + 中的解構函式  
 在 Managed Extensions，參考類別的解構函式被藉由使用下列兩個步驟：  
  
1.  在內部，重新命名的使用者提供解構函式`Finalize`。 如果類別的基底類別 （請記住，CLR 物件模型中，支援只有單一繼承），編譯器會插入下列使用者提供的程式碼執行其完成項的呼叫。 例如，請考慮下列的簡單階層從 Managed Extensions 語言規格：  
  
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
  
 在此範例中，這兩種解構函式會重新命名`Finalize`。 `B``Finalize`具有的引動過程`A`的`Finalize`方法加入下列的引動過程`WriteLine`。 這是什麼，記憶體回收行程會預設叫用在最終處理期間。 以下是此內部轉換可能如下：  
  
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
  
1.  在第二個步驟中，編譯器會合成虛擬解構函式。 此解構函式是什麼 Managed Extensions 使用者程式叫用直接或透過刪除運算式的應用程式。 它是由記憶體回收行程永遠不會叫用。  
  
     兩個陳述式會放置於此合成解構函式內。 其中一個是呼叫`GC::SuppressFinalize`以確定的任何多個引動過程`Finalize`。 第二個是實際叫用`Finalize`，表示該類別的使用者提供解構函式。 以下是這可能會看起來像：  
  
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
  
 這個實作可讓使用者明確叫用類別時`Finalize`方法現在而非每次您有沒有控制權，它不會不真的繫結中使用`Dispose`方法方案。 Visual c + + 會變更。  
  
## <a name="destructors-in-new-syntax"></a>在新語法的解構函式  
 在新語法中，解構函式已重新命名為內部`Dispose`實作的方法，並參考類別自動擴充`IDispose`介面。 也就是說，在 Visual c + + 中，我們對類別會轉換，如下所示：  
  
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
  
 當任一解構函式會明確地叫用在新語法中，或`delete`套用至追蹤控制代碼，基礎`Dispose`自動叫用方法。 如果它是在衍生的類別呼叫`Dispose`基底類別方法會插入在結束時的合成方法。  
  
 但這不會取得我們到具決定性最終處理。 為了達成此目標，我們需要額外的本機參考物件的支援。 （這具有內受管理的擴充功能，沒有類似的支援，因此它不轉譯問題。）  
  
## <a name="declaring-a-reference-object"></a>宣告的參考物件  
 Visual c + + 支援的宣告參考類別的物件上本機堆疊，或做為類別成員，就好像直接存取。 結合具有解構函式的關聯時`Dispose`方法，結果是參考型別上的最終處理語意的自動引動過程。  
  
 首先，我們定義參考類別的物件建立做為透過其類別建構函式的資源擷取。 其次，類別解構函式中釋放物件建立時所取得的資源。  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 在本機使用的型別名稱，但沒有伴隨 hat 宣告物件。 所有使用該物件，例如，叫用方法，都透過成員選取點 (`.`) 而不是箭號 (`->`)。 在區塊的結尾，相關聯的解構函式，會轉換成`Dispose`，會自動叫用，如下所示：  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 如同`using`C# 中的陳述式，這不會不對抗所有參考類型的基礎 CLR 條件約束必須先在 CLR 堆積配置。 基礎語意維持不變。 使用者可能已撰寫下列對等程式碼 （和這可能是由編譯器執行內部轉換）：  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 作用中，在新語法中，解構函式會一次與配對建構函式做為自動取得/釋放機制繫結至本機物件的存留期。  
  
## <a name="declaring-an-explicit-finalize"></a>宣告明確的 Finalize  
 在新語法中，如我們所見，解構函式合成到`Dispose`方法。 這表示，解構函式未明確地叫用時，記憶體回收行程，最終處理期間不會如往常一般尋找相關聯`Finalize`物件方法。 若要支援解構和最終處理，我們引進特殊的語法，來提供完成項。 例如:   
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!`前置詞相當於波狀符號 (`~`) 類別的解構函式時導致-也就是這兩種後的存留期方法的類別名稱前面加上的語彙基元。 如果合成`Finalize`方法，就會發生在衍生類別的基底類別的引動過程`Finalize`方法會在它的結尾插入。 如果明確叫用解構函式時，會隱藏完成項。 以下是轉換可能如下：  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>從 Managed Extensions for c + + 移至 Visual c + + 2010  
 每當參考類別包含非一般解構函式時，它會編譯 Visual c + + 在 c + + 程式的受管理的擴充功能的執行階段行為會變更。 必要的轉換演算法是如下所示：  
  
1.  如果解構函式存在，請重寫，類別完成項。  
  
2.  如果`Dispose`方法存在，則將它重寫成類別解構函式。  
  
3.  如果解構函式存在，但是沒有任何`Dispose`方法，執行第一個項目時保留解構函式。  
  
 在新語法，從 Managed Extensions 移動您的程式碼，您可能會遺失執行此轉換。 如果應用程式是以某種方式依存於相關聯的最終處理方法的執行，會以無訊息模式與您的預期的不同應用程式的行為。  
  
## <a name="see-also"></a>請參閱  
 [Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)   
 [解構函式與完成項中如何： 定義和使用類別和結構 (C + + /CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)