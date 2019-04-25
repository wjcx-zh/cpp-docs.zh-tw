---
title: C 的 Microsoft 擴充功能和C++
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: dab8ac23be8b66ca84c57514c6c04e94dddebaae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321185"
---
# <a name="microsoft-extensions-to-c-and-c"></a>C 的 Microsoft 擴充功能和C++

Visual C++ 擴充 ANSI C 和 ANSI C++ 標準如下。

## <a name="keywords"></a>關鍵字

加入數個關鍵字。 在清單中[關鍵字](../../cpp/keywords-cpp.md)，有兩個前置底線關鍵字是視覺效果C++擴充功能。

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>從類別定義的靜態 const 整數 （或列舉） 成員

在標準 (**/Za**)，您必須進行類別外定義之資料成員，如下所示：

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

底下 **/Ze**，層級定義為靜態、 const 整數和 const enum 資料成員的選擇性。 只有靜態和常數的整數和列舉可以在類別之內有初始設定式；初始設定運算式必須是常數運算式。

若要避免發生錯誤，提供在標頭檔和標頭檔包含多個原始程式檔中的層級定義時，使用[selectany](../../cpp/selectany.md)。 例如：

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>轉型

C++ 編譯器和 C 編譯器都支援這些類型的非 ANSI 轉換：

- 非 ANSI 轉換產生左值 (L-Value)。 例如: 

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > 此擴充功能只能在 C 語言中使用。 您可以在 C++ 程式碼中使用下列 ANSI C 標準格式修改指標，就好像這是不同類型的指標。

   前面的範例可以重寫如下，以符合 ANSI C 標準。

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- 從函式指標至資料指標的非 ANSI 轉換。 例如: 

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   若要執行同樣的轉換同時又維持 ANSI 相容性，您必須在將函式指標轉換為資料指標之前先將它轉換為 `uintptr_t`：

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>可變長度引數清單

C++ 編譯器和 C 編譯器都支援指定可變引數數目的函式宣告子，後面接著一個改為提供類型的函式定義：

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>單行註解

C 編譯器支援由兩個正斜線 (//) 字元引入的單行註解：

```C
// This is a single-line comment.
```

## <a name="scope"></a>範圍

C 編譯器支援下列範圍相關功能。

- 重複定義為靜態的外部項目：

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- 良性的 typedef 的重新定義相同的範圍內的使用：

   ```C
   typedef int INT;
   typedef int INT;
   ```

- 函式宣告子具有檔案範圍：

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- 透過使用非常數運算式初始化的區塊範圍變數的使用：

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>資料宣告和定義

C 編譯器支援下列資料宣告和定義功能。

- 混合的字元和字串常數初始設定式中：

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- 位元欄位，而不具有基底型別**不帶正負號的 int**或是**帶正負號 int**。

- 沒有類型的宣告子：

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- 為結構和等位的最後一個欄位的可變大小的陣列：

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- 未命名 （匿名） 的結構：

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- 未命名的 （匿名） 等位：

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- 未命名的成員：

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>內建函式的浮點函式

X86C++編譯器和 C 編譯器支援內嵌產生`atan`， `atan2`， `cos`， `exp`， `log`， `log10`， `sin`， `sqrt`，以及`tan`函式時 **/Oi**指定。 對於 C 編譯器，使用這些內建函式時會失去 ANSI 一致性，因為它們不會設定 `errno` 變數。

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>將非 const 指標參數傳遞至函式必須要有 const 的指標參數的參考

這是延伸C++。 此程式碼將會以編譯 **/Ze**:

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646。H 未啟用

底下 **/Ze**，您必須包含 iso646.h>，如果您想要使用下列運算子的文字形式：

- & & (and)

- &= (and_eq)

- & (bitand)

- &#124;(bitor)

- ~ (compl)

- ! (not)

- != (not_eq)

- &#124;&#124;（或者）

- &#124;= (or_eq)

- ^ (xor)

- ^ = (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>字串常值的位址必須是類型 const char []，非 const char （*）]

下列範例會輸出`char const (*)[4]`底下 **/Za**，但`char const [4]`之下 **/Ze**。

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>另請參閱

- [/Za、/Ze (停用語言延伸模組)](za-ze-disable-language-extensions.md)
- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
