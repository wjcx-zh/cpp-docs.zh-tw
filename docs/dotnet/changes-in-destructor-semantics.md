---
title: 解構函式語意的變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c25045291afed1e8072867ee668716b2f396ef30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420019"
---
# <a name="changes-in-destructor-semantics"></a>解構函式語意的變更

對於類別解構函式的語意已大幅變更從 Managed Extensions for c + + Visual c + +。

管理擴充功能中參考類別內，但不是會在實值類別允許類別解構函式。 這並未變更新語法中。 不過，已變更類別的解構函式的語意。 本主題著重於的原因而變更，並討論它如何影響現有的 CLR 程式碼的轉譯。 它可能是語言的兩個版本之間的最重要的程式設計人員層級變更。

## <a name="non-deterministic-finalization"></a>不具決定性的最終處理

與物件相關聯的記憶體回收的記憶體回收行程，相關聯之前`Finalize`，如果有的話，會叫用方法。 您可以將這個方法視為一種進階的解構函式因為它未繫結至程式物件的存留期。 我們把這稱為最終處理。 時間只是當或甚至是否`Finalize`叫用方法未定義。 這是什麼意思是說回收表現不具決定性的最終處理。

不具決定性的最終處理適用於動態記憶體管理。 當可用記憶體不足時，記憶體回收行程就會執行。 環境中，在記憶體回收以釋放記憶體的解構函式是不必要的收集。 不具決定性的最終處理不會無法正常運作，不過，當物件會維護重要的資源，例如資料庫連接或某種形式的鎖定。 在此情況下，我們應該儘速釋放該資源。 在原生世界中，所使用的建構函式/解構函式組達成。 只要物件的存留期結束時，在其中宣告本機區塊結束時，或解開堆疊時擲回的例外狀況，因為解構函式執行，就會自動釋放資源。 這種方法非常適合，和我們真的迫切錯過它在受管理的擴充功能並不存在。

CLR 所提供的解決方案是讓類別來實作`Dispose`方法的`IDisposable`介面。 此處的問題在於`Dispose`需要使用者的明確引動過程。 這是容易發生錯誤。 C# 語言提供適度的一種特殊形式的自動化`using`陳述式。 Managed Extensions 設計提供任何特殊的支援。

## <a name="destructors-in-managed-extensions-for-c"></a>Managed Extensions for c + + 中的解構函式

管理擴充功能中參考類別的解構函式被藉由使用下列兩個步驟：

1. 在內部為重新命名的使用者提供解構函式`Finalize`。 如果該類別的基底類別 （請記住，CLR 物件模型中，只能使用單一繼承支援），編譯器會插入下列使用者提供的程式碼執行其完成項呼叫。 例如，請考慮下列的簡單階層取自 Managed Extensions 語言規格：

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

在此範例中，這兩種解構函式會重新命名`Finalize`。 `B``Finalize`擁有的引動過程`A`的`Finalize`方法已加入下列的引動過程`WriteLine`。 這是什麼，記憶體回收行程會預設叫用在最終處理期間。 以下是此內部轉換可能會如下所示：

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

1. 在第二個步驟中，編譯器會合成虛擬解構函式。 此解構函式是什麼我們 Managed Extensions 的使用者方案叫用直接或透過刪除運算式的應用程式。 它是由記憶體回收行程永遠不會叫用。

     兩個陳述式都位於此合成的解構函式。 其中一個會呼叫`GC::SuppressFinalize`並確定有沒有更多的引動過程的`Finalize`。 第二個是實際叫用`Finalize`，代表該類別的使用者提供解構函式。 以下是這可能會如下所示：

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

雖然這個實作可讓使用者明確叫用類別`Finalize`方法現在而非每次您有沒有任何控制項，它不會不真的將繫結中使用`Dispose`方法解決方案。 這是 Visual c + + 中進行變更。

## <a name="destructors-in-new-syntax"></a>在新語法中的解構函式

在新語法中，解構函式已重新命名為內部`Dispose`方法，並參考類別自動擴充來實作`IDispose`介面。 也就是在 Visual c + + 中，我們對類別，會轉換，如下所示：

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

當其中一個解構函式會明確地叫用在新語法中，或當`delete`套用至追蹤控制代碼，基礎`Dispose`會自動叫用方法。 如果它是在衍生的類別呼叫`Dispose`基底類別方法會插入在合成的方法。

但這不會取得我們一直到具決定性最終處理。 為了達成此目標，我們需要本機參考物件的額外的支援。 （這具有管理延伸模組內不類似的支援，因此它不轉譯問題。）

## <a name="declaring-a-reference-object"></a>宣告的參考物件

Visual c + + 支援的宣告參考類別的物件上的本機堆疊或類別的成員，就好像直接存取。 結合具有解構函式的關聯時`Dispose`結果的方法是參考型別上的最終處理語意的自動引動過程。

首先，我們定義我們參考類別，使物件建立做為資源，以透過其類別建構函式取得。 其次，在類別解構函式中，我們發行物件建立時所取得的資源。

```
public ref class R {
public:
   R() { /* acquire expensive resource */ }
   ~R() { /* release expensive resource */ }

   // everything else...
};
```

在本機使用的型別名稱，但不含隨附的帽子宣告物件。 所有使用該物件，例如，叫用方法，都透過成員選取點 (`.`) 而不是箭號 (`->`)。 在區塊的結束時，相關聯的解構函式，轉換成`Dispose`，會自動叫用，如下所示：

```
void f() {
   R r;
   r.methodCall();

   // r is automatically destructed here -
   // that is, r.Dispose() is invoked
}
```

如同`using`C# 中的陳述式，這不會不對抗所有參考型別的基礎 CLR 條件約束必須在 CLR 堆積配置。 基礎語意維持不變。 使用者可能已撰寫下列對等程式碼 （和這可能是由編譯器執行內部轉換）：

```
// equivalent implementation
// except that it should be in a try/finally clause
void f() {
   R^ r = gcnew R;
   r->methodCall();

   delete r;
}
```

在新語法中，解構函式會重新建構函式搭檔，為 自動取得/釋放機制繫結至本機物件的存留期。

## <a name="declaring-an-explicit-finalize"></a>宣告明確的 Finalize

在新語法中，如我們所見，解構函式合成為`Dispose`方法。 這表示，解構函式未明確地叫用時，記憶體回收行程，最終處理期間不會如往常尋找相關聯`Finalize`物件的方法。 若要支援解構和最終處理，我們引進了特殊的語法，以提供完成項。 例如: 

```
public ref class R {
public:
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }
};
```

`!`前置詞相當於波狀符號 (`~`) 導入類別的解構函式-也就是這兩個後置的生命週期方法前面加上類別的名稱語彙基元。 如果合成`Finalize`方法，就會發生在衍生類別中，基底類別的引動過程`Finalize`方法會在它的結尾插入。 如果明確地叫用解構函式時，會隱藏的完成項。 以下是轉換可能會如下所示：

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

每當參考類別包含非一般的解構函式時，它會編譯 Visual c + + 底下之 Managed Extensions for c + + 程式的執行階段行為會變更。 必要的轉換演算法是如下所示：

1. 如果解構函式存在時，重寫成類別完成項。

1. 如果`Dispose`方法存在，則將它重寫成的類別解構函式。

1. 如果解構函式存在，但是沒有任何`Dispose`方法，在執行第一個項目時保留解構函式。

在新的語法，從 Managed Extensions 移動您的程式碼，您可能會遺失執行此轉換。 如果應用程式必須以某種方式依賴執行相關聯的最終處理方法，將以無訊息模式會從您的預期不同應用程式的行為。

## <a name="see-also"></a>另請參閱

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[解構函式和完成項中如何： 定義和使用類別和結構 (C + + /cli CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)