---
title: CLR 參考類別物件的宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3e8ec6407e12d0c26331d45dc1659277feed016
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444576"
---
# <a name="declaration-of-a-clr-reference-class-object"></a>CLR 參考類別物件的宣告

語法來宣告和具現化參考類別類型的物件已從 Managed Extensions for c + + Visual c + +。

在 Managed Extensions，ISO c + + 指標語法中，使用的選擇性使用宣告參考類別類型物件`__gc`左邊的星形的關鍵字 (`*`)。 例如，以下是參考的各種不同類別類型物件宣告在 Managed Extensions 語法中：

```
public __gc class Form1 : public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container __gc *components;
   Button __gc *button1;
   DataGrid __gc *myDataGrid;
   DataSet __gc *myDataSet;

   void PrintValues( Array* myArr ) {
      System::Collections::IEnumerator* myEnumerator =
         myArr->GetEnumerator();

      Array *localArray;
      myArr->Copy(myArr, localArray, myArr->Length);
   }
};
```

您可以在新語法中，宣告參考類別類型物件來使用新的宣告式權杖 (`^`) 稱為正式*追蹤控制代碼*以及非正式地*hat*。 （表示參考型別位於 CLR 堆積，並可因此無障礙地壓縮期間移動位置記憶體回收集合堆積追蹤形容詞。 執行階段期間，會以透明的方式更新的追蹤控制代碼。 兩個類似的概念並*追蹤參考*(`%`)，而*內部指標*(`interior_ptr<>`)，在中所述[實值類型語意](../dotnet/value-type-semantics.md)。

若要移動的宣告式語法與 ISO c + + 指標語法的重複使用的主要原因如下所示：

- 使用指標的語法不允許多載的運算子，以直接套用到參考的物件。 相反地，其中必須使用其內部的名稱，例如呼叫運算子`rV1->op_Addition(rV2)`而不是更具直覺性`rV1+rV2`。

- 許多指標作業，例如轉型和指標算術來存放在記憶體回收的物件不允許收集堆積。 更好的追蹤控制代碼的概念會擷取 CLR 參考類型的本質。

`__gc`的追蹤控制代碼修飾詞是不必要的而且不支援。 使用物件本身不會變更;它仍會透過指標成員選取運算子存取成員 (`->`)。 例如，以下是上述 Managed Extensions 程式碼範例，轉譯成新的語法：

```
public ref class Form1: public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container^ components;
   Button^ button1;
   DataGrid^ myDataGrid;
   DataSet^ myDataSet;

   void PrintValues( Array^ myArr ) {
      System::Collections::IEnumerator^ myEnumerator =
         myArr->GetEnumerator();

      Array ^localArray;
      myArr->Copy(myArr, localArray, myArr->Length);   }
};
```

## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>在 CLR 堆積上物件的動態配置

在 受管理的擴充功能，有兩個`new`運算式之間的原生和 managed 堆積配置是透明化。 在幾乎所有情況下，編譯器就能夠使用內容來判斷是否要從原生或 managed 堆積配置記憶體。 例如，套用至物件的

```
Button *button1 = new Button; // OK: managed heap
int *pi1 = new int;           // OK: native heap
Int32 *pi2 = new Int32;       // OK: managed heap
```

當您不想內容的堆積配置時，您無法直接使用編譯器`__gc`或`__nogc`關鍵字。 在新語法中，不同性質的兩個新的運算式會採用明確`gcnew`關鍵字。 例如，先前的三個宣告新語法中看起來如下所示：

```
Button^ button1 = gcnew Button;        // OK: managed heap
int * pi1 = new int;                   // OK: native heap
Int32^ pi2 = gcnew Int32; // OK: managed heap
```

以下是 Managed Extensions 初始化`Form1`上一節中所宣告的成員：

```
void InitializeComponent() {
   components = new System::ComponentModel::Container();
   button1 = new System::Windows::Forms::Button();
   myDataGrid = new DataGrid();

   button1->Click +=
      new System::EventHandler(this, &Form1::button1_Click);
}
```

以下是重新轉換成新的語法相同的初始設定。 請注意，hat 並不需要參考類型時的目標`gcnew`運算式。

```
void InitializeComponent() {
   components = gcnew System::ComponentModel::Container;
   button1 = gcnew System::Windows::Forms::Button;
   myDataGrid = gcnew DataGrid;

   button1->Click +=
      gcnew System::EventHandler( this, &Form1::button1_Click );
}
```

## <a name="a-tracking-reference-to-no-object"></a>沒有物件的追蹤參考

在新語法中，`0`不再代表 null 的地址，但會被視為一個整數，與相同`1`， `10`，或`100`。 新的特殊權杖產生的追蹤參考 null 值。 比方說，管理擴充功能中初始化參考類型，來不解決任何物件，如下所示：

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

在新語法中，初始化或指派值的輸入以`Object`會導致該實值型別的隱含 boxing。 在新語法中，同時`obj`和`obj2`會初始化為定址 boxed 的 Int32 物件分別保留 0 和 1 的值。 例如: 

```
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;
```

因此，若要執行明確的初始化、 指派及追蹤控制代碼設為 null 的比較，使用 新的關鍵字`nullptr`。  原始範例的正確修訂版本如下所示：

```
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to a Int32^
Object ^ obj2 = 1;
```

這變得有點現有程式碼移植到新的語法非常複雜。 例如，請考慮下列實值類別宣告：

```
__value struct Holder {
   Holder( Continuation* c, Sexpr* v ) {
      cont = c;
      value = v;
      args = 0;
      env = 0;
   }

private:
   Continuation* cont;
   Sexpr * value;
   Environment* env;
   Sexpr * args __gc [];
};
```

在這裡，兩者`args`和`env`是 CLR 參考型別。 以這兩個成員初始化`0`建構函式無法保持在轉換至新的語法不變。 相反地，他們必須變更為`nullptr`:

```
value struct Holder {
   Holder( Continuation^ c, Sexpr^ v )
   {
      cont = c;
      value = v;
      args = nullptr;
      env = nullptr;
   }

private:
   Continuation^ cont;
   Sexpr^ value;
   Environment^ env;
   array<Sexpr^>^ args;
};
```

同樣地，針對這些比較它們的成員會測試`0`必須也要比較之成員變更`nullptr`。 以下是管理擴充功能語法：

```
Sexpr * Loop (Sexpr* input) {
   value = 0;
   Holder holder = Interpret(this, input, env);

   while (holder.cont != 0) {
      if (holder.env != 0) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != 0) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

以下是修訂，將每個取代`0`執行個體與`nullptr`。 透過自動化許多翻譯工具可協助在這項轉換，如果沒有所有相符項目，包括使用的`NULL`巨集。

```
Sexpr ^ Loop (Sexpr^ input) {
   value = nullptr;
   Holder holder = Interpret(this, input, env);

   while ( holder.cont != nullptr ) {
      if ( holder.env != nullptr ) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != nullptr ) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

`nullptr`會轉換成任何指標或追蹤控制代碼型別，但不是會提升為整數型別。 例如，在下列設定中的初始化，`nullptr`只能當做初始值前兩個。

```
// OK: we set obj and pstr to refer to no object
Object^ obj = nullptr;
char*   pstr = nullptr; // 0 would also work here

// Error: no conversion of nullptr to 0
int ival = nullptr;
```

同樣地，假設多載的集的方法，如下所示：

```
void f( Object^ ); // (1)
void f( char* );   // (2)
void f( int );     // (3)
```

含有引動過程`nullptr`常值，如下所示，

```
// Error: ambiguous: matches (1) and (2)
f(  nullptr );
```

模稜兩可因為`nullptr`比對的追蹤控制代碼和一個指標，而且沒有提供一種類型的其他任何喜好設定。 （這種情況下會需要明確轉型以釐清）。

含有引動過程`0`完全相符項目執行個體 (3):

```
// OK: matches (3)
f( 0 );
```

因為`0`屬於整數型別。 已`f(int)`不存在，該呼叫會明確地比對`f(char*)`透過標準的轉換。 比對的規則提供完全相符的優先順序高於標準轉換。 如果沒有完全相符，標準的轉換會優先於實值型別的隱含 boxing。 這就是為什麼沒有任何模稜兩可。

## <a name="see-also"></a>另請參閱

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)