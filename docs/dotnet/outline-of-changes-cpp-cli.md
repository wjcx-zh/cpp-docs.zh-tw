---
title: "變更大綱 (C++/CLI) | Microsoft Docs"
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
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 變更大綱 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個大綱顯示從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，語言中一些變更的範例。  如需詳細資訊，請遵循每個項目隨附的連結。  
  
## 無雙底線關鍵字  
 所有關鍵字前面的雙底線都已移除，只有一個例外。  所以，`__value` 變成 `value`，而 `__interface` 變成 `interface` 等等。  若要避免使用者程式碼中的關鍵字與識別項之間出現名稱衝突，就要先將關鍵字視為內容。  
  
 如需詳細資訊，請參閱[語言關鍵字 \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md)。  
  
## 類別宣告  
 Managed Extensions 語法：  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 新的語法：  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 如需詳細資訊，請參閱[Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)。  
  
## 物件宣告  
 Managed Extensions 語法：  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 新的語法：  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 如需詳細資訊，請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
### Managed 堆積配置  
 Managed Extensions 語法：  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 新的語法：  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 如需詳細資訊，請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
### No 物件的追蹤參考  
 Managed Extensions 語法：  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 新的語法：  
  
```  
// Incorrect Translation  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
  
// Correct Translation  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to an Int32^  
Object ^ obj2 = 1;  
```  
  
 如需詳細資訊，請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
## 陣列宣告  
 CLR 陣列已重新設計。  它類似 stl `vector` 範本集合，但是會對應至基礎 `System::Array` 類別，也就是說，它不是範本實作。  
  
 如需詳細資訊，請參閱[CLR 陣列的宣告](../dotnet/declaration-of-a-clr-array.md)。  
  
### 將陣列當做參數  
 Managed Extensions 陣列語法：  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 新的陣列語法：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### 將陣列當做傳回型別  
 Managed Extensions 陣列語法：  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 新的陣列語法：  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### 本機 CLR 陣列的縮寫初始化  
 Managed Extensions 陣列語法：  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 新的陣列語法：  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### 明確的 CLR 陣列宣告  
 Managed Extensions 陣列語法：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 新的陣列語法：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 新加入語言：在 gcnew 之後的明確陣列初始化  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## 純量屬性  
 Managed Extensions 屬性語法：  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 新的屬性語法：  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon …  
};  
```  
  
 新加入語言：trivial 屬性  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 如需詳細資訊，請參閱[屬性宣告](../dotnet/property-declaration.md)。  
  
## 索引屬性  
 Managed Extensions 索引屬性語法：  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 新的索引屬性語法：  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 新加入語言：類別層級索引屬性  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 如需詳細資訊，請參閱[屬性索引宣告](../dotnet/property-index-declaration.md)。  
  
## 多載運算子  
 Managed Extensions 運算子多載語法：  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
};  
  
int main() {  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc = Vector::op_Division( pa, 4.8916 );  
  
   if ( Vector::op_Equality( pa, pc ))  
      ;  
}  
```  
  
 新的運算子多載語法：  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
};  
  
int main() {  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );  
  
   Vector^ pc = pa / 4.8916;  
   if ( pc == pa )  
      ;  
}  
```  
  
 如需詳細資訊，請參閱[多載運算子](../dotnet/overloaded-operators.md)。  
  
## 轉換運算子  
 Managed Extensions 轉換運算子語法：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 新的轉換運算子語法：  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 如需詳細資訊，請參閱[轉換運算子的變更](../dotnet/changes-to-conversion-operators.md)。  
  
## 介面成員的明確覆寫  
 Managed Extensions 明確覆寫語法：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 新的明確覆寫語法：  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 如需詳細資訊，請參閱[介面成員的明確覆寫](../dotnet/explicit-override-of-an-interface-member.md)。  
  
## 私用虛擬函式  
 Managed Extensions 私用虛擬函式語法：  
  
```  
__gc class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
__gc class Derived : public Base {  
public:  
   // ok: g() overrides Base::g()  
   virtual void g();  
};  
```  
  
 新的私用虛擬函式語法  
  
```  
ref class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
ref class Derived : public Base {  
public:  
   // error: cannot override: Base::g() is inaccessible  
   virtual void g() override;  
};  
```  
  
 如需詳細資訊，請參閱[私用虛擬函式](../dotnet/private-virtual-functions.md)。  
  
## CLR 列舉型別  
 Managed Extensions 列舉語法：  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};    
```  
  
 新的列舉語法：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 除了這個小小的語法變更以外，CLR 列舉型別的行為在不同方面也有所變更：  
  
-   不再支援 CLR 列舉的向前宣告。  
  
-   內建算術型別和 Object 類別階層之間的多載解析，已於 Managed Extensions 和 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之間回復。  副作用是，CLR 列舉無法再隱含地轉換成算術型別。  
  
-   在新語法中，CLR 列舉會維護本身的範圍，但在 Managed Extensions 則不是如此。  先前，列舉值在列舉的包含範圍中是可見的；而現在，列舉值在列舉範圍內是封裝的。  
  
 如需詳細資訊，請參閱[CLR 列舉類型](../dotnet/clr-enum-type.md)。  
  
## 移除 \_\_box 關鍵字  
 Managed Extensions Boxing 語法：  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 新的 Boxing 語法：  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 如需詳細資訊，請參閱[Boxed 值的追蹤控制代碼](../dotnet/a-tracking-handle-to-a-boxed-value.md)。  
  
## Pin 指標  
 Managed Extensions Pin 指標語法：  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 新的 Pin 指標語法：  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 如需詳細資訊，請參閱[實值類型語意](../dotnet/value-type-semantics.md)。  
  
## \_\_typeof 關鍵字變成 typeid  
 Managed Extensions typeof 語法：  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 新的 typeid 語法：  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 如需詳細資訊，請參閱[typeof 變成 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)。  
  
## 請參閱  
 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-tw/edbded88-7ef3-4757-bd9d-b8f48ac2aada)   
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)