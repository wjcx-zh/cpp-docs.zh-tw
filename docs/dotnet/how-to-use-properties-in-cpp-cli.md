---
title: "如何：在 C++/CLI 中使用屬性 | Microsoft Docs"
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
  - "屬性 [C++], 簡單"
  - "簡單屬性"
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將 C\+\+\/CLI 將示範如何使用屬性。  
  
## 基底屬性  
 對於基本屬性那些該只指定及擷取成員您不需要明確定義 get 和 set 存取子函式的私用資料，因為編譯器會自動提供這些屬性，將屬性的資料型別。  這個程式碼會示範基本屬性:  
  
```  
// SimpleProperties.cpp  
// compile with: /clr  
using namespace System;  
  
ref class C {  
public:  
   property int Size;  
};  
  
int main() {  
   C^ c = gcnew C;  
   c->Size = 111;  
   Console::WriteLine("c->Size = {0}", c->Size);  
}  
```  
  
 **Output**  
  
  **C\# 大小\>\= 111**   
## 靜態屬性  
 這個程式碼範例示範如何宣告和使用一個靜態屬性。一個靜態屬性只能存取該類別的靜態成員。  
  
```  
// mcppv2_property_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class StaticProperties {  
   static int MyInt;  
   static int MyInt2;  
  
public:  
   static property int Static_Data_Member_Property;  
  
   static property int Static_Block_Property {  
      int get() {  
         return MyInt;  
      }  
  
      void set(int value) {  
         MyInt = value;  
      }        
   }  
};  
  
int main() {  
   StaticProperties::Static_Data_Member_Property = 96;  
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);  
  
   StaticProperties::Static_Block_Property = 47;  
   Console::WriteLine(StaticProperties::Static_Block_Property);  
}  
```  
  
 **Output**  
  
  **96**  
**47**   
## 索引屬性  
 索引的屬性通常會使用其他的運算子，存取的資料結構。  
  
 如果您正在使用預設索引屬性，您可以參考類別名稱存取資料結構，，但是，如果您使用使用者定義的索引屬性，您必須指定屬性名稱存取資料結構。  
  
 使用 `this` 指標，如需如何存取預設索引子的詳細資訊，請參閱 [實值類型和參考類型中 this 指標的語意](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md)。  
  
 如需如何使用以 C\# 撰寫的索引子的詳細資訊，請參閱 [如何：使用 C\# 索引子](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md)。  
  
 這個程式碼範例示範如何使用預設和使用者定義的索引屬性:  
  
```  
// mcppv2_property_2.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   array<int>^ MyArr;  
  
public:  
   C() {  
      MyArr = gcnew array<int>(5);  
   }  
  
   // default indexer  
   property int default[int] {  
      int get(int index) {  
         return MyArr[index];  
      }  
      void set(int index, int value) {  
         MyArr[index] = value;  
      }  
   }  
  
   // user-defined indexer  
   property int indexer1[int] {  
      int get(int index) {  
         return MyArr[index];  
      }  
      void set(int index, int value) {  
         MyArr[index] = value;  
      }  
   }  
};  
  
int main() {  
   C ^ MyC = gcnew C();  
  
   // use the default indexer  
   Console::Write("[ ");  
   for (int i = 0 ; i < 5 ; i++) {  
      MyC[i] = i;  
      Console::Write("{0} ", MyC[i]);  
   }  
  
   Console::WriteLine("]");  
  
   // use the user-defined indexer  
   Console::Write("[ ");  
   for (int i = 0 ; i < 5 ; i++) {  
      MyC->indexer1[i] = i * 2;  
      Console::Write("{0} ", MyC->indexer1[i]);  
   }  
  
   Console::WriteLine("]");  
}  
```  
  
 **Output**  
  
  **\[ 0 1 2 3 4 \]**  
**\[ 0 2 4 6 8 \]** 使用 `this` 指標，下一個範例示範如何呼叫預設索引子。  
  
```  
// call_default_indexer_through_this_pointer.cpp  
// compile with: /clr /c  
value class Position {  
public:  
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {  
      this->default[x, y] = 1;  
   }  
  
   property int default[int, int] {  
      int get(int x, int y) {  
         return position[x, y];  
      }  
  
      void set(int x, int y, int value) {}  
   }  
  
private:  
   array<int, 2> ^ position;  
};  
```  
  
 這個範例示範如何使用 <xref:System.Reflection.DefaultMemberAttribute> 指定預設索引子:  
  
```  
// specify_default_indexer.cpp  
// compile with: /LD /clr  
using namespace System;  
[Reflection::DefaultMember("XXX")]  
public ref struct Squares {  
   property Double XXX[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
```  
  
 在上述範例中建立的下一個範例使用中繼資料。  
  
```  
// consume_default_indexer.cpp  
// compile with: /clr  
#using "specify_default_indexer.dll"  
int main() {  
   Squares ^ square = gcnew Squares();  
   System::Console::WriteLine("{0}", square[3]);  
}  
```  
  
 **Output**  
  
 **9**   
## 虛擬屬性  
 這個程式碼範例示範如何宣告和使用虛擬屬性:  
  
```  
// mcppv2_property_4.cpp  
// compile with: /clr  
using namespace System;  
interface struct IEFace {  
public:  
   property int VirtualProperty1;  
   property int VirtualProperty2 {  
      int get();  
      void set(int i);  
   }  
};  
  
// implement virtual events  
ref class PropImpl : public IEFace {  
   int MyInt;  
public:  
   virtual property int VirtualProperty1;  
  
   virtual property int VirtualProperty2 {  
      int get() {  
         return MyInt;  
      }  
      void set(int i) {  
         MyInt = i;  
      }  
   }  
};  
  
int main() {  
   PropImpl ^ MyPI = gcnew PropImpl();  
   MyPI->VirtualProperty1 = 93;  
   Console::WriteLine(MyPI->VirtualProperty1);  
  
   MyPI->VirtualProperty2 = 43;  
   Console::WriteLine(MyPI->VirtualProperty2);  
}  
```  
  
 **Output**  
  
  **93**  
**43**   
## 抽象和密封屬性  
 雖然 [abstract](../windows/abstract-cpp-component-extensions.md) 和 [sealed](../windows/sealed-cpp-component-extensions.md) 關鍵字指定，因為在 ECMA C\+\+\/CLI 規格的有效，的 Visual C\+\+ 編譯器，您無法指定它們在一般屬性，也不是一個重要屬性的屬性宣告。  
  
 若要宣告密封或抽象屬性，您可以在 get 和 set 存取子函式必須定義一個重要的屬性會指定 `abstract` 或 `sealed` 關鍵字。  
  
```  
// properties_abstract_sealed.cpp  
// compile with: /clr  
ref struct A {  
protected:  
   int m_i;  
  
public:  
   A() { m_i = 87; }  
  
   // define abstract property  
   property int Prop_1 {  
      virtual int get() abstract;  
      virtual void set(int i) abstract;  
   }  
};  
  
ref struct B : A {  
private:  
   int m_i;  
  
public:  
   B() { m_i = 86; }  
  
   // implement abstract property  
   property int Prop_1 {  
      virtual int get() override { return m_i; }  
      virtual void set(int i) override { m_i = i; }  
   }  
};  
  
ref struct C {  
private:  
   int m_i;  
  
public:  
   C() { m_i = 87; }  
  
   // define sealed property  
   property int Prop_2 {  
      virtual int get() sealed { return m_i; }  
      virtual void set(int i) sealed { m_i = i; };  
   }  
};  
  
int main() {  
   B b1;  
   // call implementation of abstract property  
   System::Console::WriteLine(b1.Prop_1);  
  
   C c1;  
   // call sealed property  
   System::Console::WriteLine(c1.Prop_2);  
}  
```  
  
 **Output**  
  
  **86**  
**87**   
## 多維屬性  
 您可以使用多維屬性定義屬性接受非標準數字的存取子方法。  
  
```  
// mcppv2_property_5.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(0) {}  
   property double MultiDimProp[int, int, int] {  
      double get(int, int, int) {  
         return d;  
      }  
      void set(int i, int j, int k, double l) {  
         // do something with those ints  
         d = l;  
      }  
   }  
  
   property double MultiDimProp2[int] {  
      double get(int) {  
         return d;  
      }  
      void set(int i, double l) {  
         // do something with those ints  
         d = l;  
      }  
   }  
  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   MyX->MultiDimProp[0,0,0] = 1.1;  
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);  
}  
```  
  
 **Output**  
  
  **1.1**   
## 多載化、屬性存取子  
 下列範例說明如何多載索引屬性。  
  
```  
// mcppv2_property_6.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(0.0) {}  
   property double MyProp[int] {  
      double get(int i) {  
         return d;  
      }  
  
      double get(System::String ^ i) {  
         return 2*d;  
      }  
  
      void set(int i, double l) {  
         d = i * l;  
      }  
   }   // end MyProp definition  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   MyX->MyProp[2] = 1.7;  
   System::Console::WriteLine(MyX->MyProp[1]);  
   System::Console::WriteLine(MyX->MyProp["test"]);  
}  
```  
  
 **Output**  
  
  **3.4**  
**6.8**   
## 請參閱  
 [property](../windows/property-cpp-component-extensions.md)