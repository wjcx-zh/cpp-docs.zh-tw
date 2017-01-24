---
title: "CLR 參考類別物件的宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考類型, CLR"
  - "類型 [C++], 參考類型"
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLR 參考類別物件的宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，宣告和產生參考類別型別之物件的語法已變更。  
  
 在 Managed Extensions 中，會使用 ISO\-C\+\+ 指標語法宣告參考類別型別物件，而且可以選擇將 `__gc` 關鍵字放在星號 \(`*`\) 左邊。  例如，下列是在 Managed Extensions 語法中的各種參考類別型別物件宣告：  
  
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
  
 在新語法中，您會使用新的宣告式語彙基元 \(Token\) \(`^`\) 宣告參考類別型別物件。這個語彙基元的正式名稱是「*追蹤控制代碼*」\(Tracking Handle\)，但是通常會非正式地叫做「*帽型符號*」\(Hat\)\(追蹤這個形容詞表示參考型別位於 CLR 堆積中，因此在記憶體回收堆積壓縮期間可以無障礙地移動位置\)。  追蹤控制代碼在執行階段會無障礙地進行更新。  在[實值類型語意](../dotnet/value-type-semantics.md)中會討論下列兩個相似的概念：「*追蹤參考*」\(`%`\) 和「*內部指標*」\(`interior_ptr<>`\)。  
  
 要從重複使用 ISO\-C\+\+ 指標語法中移出宣告式語法，主要的原因如下：  
  
-   使用指標語法不允許將多載運算子直接套用到參考物件。  相反地，您必須使用運算子的內部名稱來呼叫該運算子，例如使用 `rV1->op_Addition(rV2)`，而不是比較容易了解的 `rV1+rV2`。  
  
-   記憶體回收堆積上儲存的物件不允許進行一些指標作業，例如轉型和指標算術。  追蹤控制代碼的概念比較能夠表達 CLR 參考型別的本質。  
  
 不需要而且不支援追蹤控制代碼上的 `__gc` 修飾詞 \(Modifier\)。  物件本身的用法不變，一樣是透過指標成員選取運算子 \(`->`\) 存取成員。  例如，下列是將之前的 Managed Extensions 程式碼範例轉譯成新語法：  
  
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
  
## CLR 堆積上的物件動態配置  
 在 Managed Extensions 中，是否存在兩個 `new` 運算式以便在原生和 Managed 堆積之間配置，在過去多數是一目了然的。  在幾乎任何情況下，編譯器都能夠利用內容來判斷要從原生或 Managed 堆積配置記憶體。  例如：  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 當您不想要內容堆積配置時，您可以用 `__gc` 或 `__nogc` 關鍵字指示編譯器。  在新語法中，會藉由引入 `gcnew` 關鍵字使兩個新運算式的個別本質變成明確。  例如，之前的三種宣告在新語法中看起來如下所示：  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 下列是在上面區段中宣告的 `Form1` 成員的 Managed Extensions 初始化：  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 下列是重新轉型至新語法的相同初始化。  請注意，如果參考型別是 `gcnew` 運算式的目標，則不需要帽型符號。  
  
```  
void InitializeComponent() {  
   components = gcnew System::ComponentModel::Container;  
   button1 = gcnew System::Windows::Forms::Button;  
   myDataGrid = gcnew DataGrid;  
  
   button1->Click +=   
      gcnew System::EventHandler( this, &Form1::button1_Click );  
}  
```  
  
## No 物件的追蹤參考  
 在新語法中，`0` 不再代表 Null 位址，而被視為整數，與 `1`、`10` 或 `100` 一樣。  新的特殊語彙基元 \(Token\) 代表追蹤參考的 Null 值。  例如，在 Managed Extensions 中，會初始化參考型別而不定址任何物件，如下所示：  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 在新語法中，實值型別的任何初始化或指派至 `Object` 都會產生該實值型別的隱含 Boxing。  在新語法中，`obj` 和 `obj2` 都會初始化，以分別指向值為 0 和 1 的 Boxed Int32 物件。  例如：  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 為了執行明確的初始化追蹤控制代碼、指派追蹤控制代碼，以及比較追蹤控制代碼與 Null，因此引入新關鍵字 `nullptr`。原本範例的正確修訂如下所示：  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 這樣多少都使得將現有程式碼移植至新語法更為複雜。  例如，請參考下列實值類別宣告：  
  
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
  
 此處，`args` 和 `env` 都是 CLR 參考型別。  在建構函式 \(Constructor\) 中將這兩個成員初始化為 `0`，這樣的做法在轉換至新語法時會不太一樣。  這兩個成員必須變更為 `nullptr`：  
  
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
  
 同樣地，將那些成員和 `0` 相較以進行測試的做法，也必須變成和 `nullptr` 相較。  下列是 Managed Extensions 語法：  
  
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
  
 以下是修訂，其中將出現的每個 `0` 都取代成 `nullptr`。  轉譯工具在這項轉換中助益良多，就算不是針對每次出現但也已經自動化大部分的項目，包括使用 `NULL` 巨集。  
  
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
  
 `nullptr` 會轉換為任何指標或追蹤控制代碼型別，但不會提升至整數型別。  例如，在下列初始化設定中，`nullptr` 只能當做前兩個項目的初始值。  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0 …  
int ival = nullptr;  
```  
  
 同樣地，指定方法的多載集合，如下所示：  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 使用 `nullptr` 常值 \(Literal\) 的引動過程，如下所示，  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 為模稜兩可，因為 `nullptr` 同時符合追蹤控制代碼和指標，而且兩種型別的偏好程度相同 \(這種情況會需要明確轉型以解除模稜兩可的情況\)。  
  
 使用 `0` 的引動過程完全符合執行個體 \(3\)：  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 因為 `0` 屬於整數型別。  如果沒有 `f(int)`，呼叫會透過標準轉換明確地符合 `f(char*)`。  比對規則認定完全相符的優先順序高於標準轉換。  如果缺少完全相符，則標準轉換優於實值型別的隱含 Boxing。  這就是不會模稜兩可的原因。  
  
## 請參閱  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [物件控制代碼運算子 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)