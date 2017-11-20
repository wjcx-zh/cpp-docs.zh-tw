---
title: "變更大綱 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a17ad8aca031d6345f3ded4839dbb543c1edf133
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="outline-of-changes-ccli"></a>變更大綱 (C++/CLI)
此外框會顯示某些變更的範例中的語言，從 Managed Extensions for c + +，Visual c + +。 請遵循隨附的每個項目，如需詳細資訊的連結。  
  
## <a name="no-double-underscore-keywords"></a>沒有雙底線關鍵字  
 已移除所有關鍵字前面兩個底線，有一個例外狀況。 因此，`__value`變成`value`，和`__interface`變成`interface`，依此類推。 若要避免名稱衝突之間關鍵字和使用者程式碼中的識別項，關鍵字是主要視為內容。  
  
 請參閱[語言關鍵字 (C + + /CLI)](../dotnet/language-keywords-cpp-cli.md)如需詳細資訊。  
  
## <a name="class-declarations"></a>類別宣告  
 受管理的擴充功能語法：  
  
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
  
 請參閱[Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)如需詳細資訊。  
  
## <a name="object-declaration"></a>物件宣告  
 受管理的擴充功能語法：  
  
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
  
 請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)如需詳細資訊。  
  
### <a name="managed-heap-allocation"></a>Managed 的堆積配置  
 受管理的擴充功能語法：  
  
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
  
 請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)如需詳細資訊。  
  
### <a name="a-tracking-reference-to-no-object"></a>沒有物件的追蹤參考  
 受管理的擴充功能語法：  
  
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
  
 請參閱[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)如需詳細資訊。  
  
## <a name="array-declaration"></a>陣列宣告  
 CLR 陣列已經重新設計。 類似於 stl`vector`範本集合，但對應至基礎`System::Array`類別-也就是它不是樣板實作。  
  
 請參閱[CLR 陣列的宣告](../dotnet/declaration-of-a-clr-array.md)如需詳細資訊。  
  
### <a name="array-as-parameter"></a>做為參數陣列  
 受管理的擴充功能陣列語法：  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 新陣列語法：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### <a name="array-as-return-type"></a>將陣列當做傳回型別  
 受管理的擴充功能陣列語法：  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 新陣列語法：  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### <a name="shorthand-initialization-of-local-clr-array"></a>本機 CLR 陣列的縮寫初始化  
 受管理的擴充功能陣列語法：  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 新陣列語法：  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### <a name="explicit-clr-array-declaration"></a>明確的 CLR 陣列宣告  
 受管理的擴充功能陣列語法：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 新陣列語法：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 語言的新手： 後面 gcnew 明確的陣列初始設定  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="scalar-properties"></a>純量屬性  
 受管理的擴充屬性語法：  
  
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
   } // Note: no semi-colon  
};  
```  
  
 語言的新手： trivial 屬性  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 請參閱[屬性宣告](../dotnet/property-declaration.md)如需詳細資訊。  
  
## <a name="indexed-properties"></a>索引屬性  
 Managed 的 Extensions 編製索引的屬性語法：  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 新的索引的屬性語法：  
  
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
  
 語言的新手： 類別層級索引的屬性  
  
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
  
 請參閱[屬性索引宣告](../dotnet/property-index-declaration.md)如需詳細資訊。  
  
## <a name="overloaded-operators"></a>多載運算子  
 受管理的擴充功能運算子多載語法：  
  
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
  
 請參閱[多載運算子](../dotnet/overloaded-operators.md)如需詳細資訊。  
  
## <a name="conversion-operators"></a>轉換運算子  
 受管理的擴充功能轉換運算子語法：  
  
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
  
 請參閱[變更為轉換運算子](../dotnet/changes-to-conversion-operators.md)如需詳細資訊。  
  
## <a name="explicit-override-of-an-interface-member"></a>介面成員的明確覆寫  
 Managed 的 Extensions 明確覆寫語法：  
  
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
  
 請參閱[介面成員的明確覆寫](../dotnet/explicit-override-of-an-interface-member.md)如需詳細資訊。  
  
## <a name="private-virtual-functions"></a>私用虛擬函式  
 受管理的擴充功能私用虛擬函式語法：  
  
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
  
 請參閱[私用虛擬函式](../dotnet/private-virtual-functions.md)如需詳細資訊。  
  
## <a name="clr-enum-type"></a>CLR 列舉類型  
 受管理的擴充功能列舉語法：  
  
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
  
 這個小語法變更，除了 CLR 列舉型別的行為已變更在數種方式：  
  
-   不再支援 CLR 列舉的向前宣告。  
  
-   內建算術類型和物件的類別階層架構之間的多載解析已反轉之間受管理的擴充功能和 Visual c + +。 副作用，CLR 列舉會不再隱含轉換成算術類型。  
  
-   在新語法中，CLR 列舉會維持其本身的範圍，這不是這樣，在 Managed Extensions。 列舉值之前，在包含列舉; 的範圍內為可見現在，列舉值會封裝在列舉的範圍內。  
  
 請參閱[CLR 列舉型別](../dotnet/clr-enum-type.md)如需詳細資訊。  
  
## <a name="removal-of-box-keyword"></a>移除的 __box 關鍵字  
 Boxing 語法的 managed 擴充功能：  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 新的 boxing 語法：  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 請參閱[追蹤處理為 Boxed 值](../dotnet/a-tracking-handle-to-a-boxed-value.md)如需詳細資訊。  
  
## <a name="pinning-pointer"></a>Pin 指標  
 Pin 指標語法的 managed 擴充功能：  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 新的 pin 指標語法：  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 請參閱[實值類型語意](../dotnet/value-type-semantics.md)如需詳細資訊。  
  
## <a name="typeof-keyword-becomes-typeid"></a>__typeof 關鍵字會變成 typeid  
 受管理的擴充功能 typeof 語法：  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 新的 typeid 語法：  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 請參閱[typeof 變成 t:: typeid](../dotnet/typeof-goes-to-t-typeid.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [C + + /CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)


