---
title: 與其他 .NET 程式設計語言間的互通性 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- C++, indexers
- indexers, consuming C#
- as C# keyword [C++]
- is C# keyword [C++]
- lock statement
- lock C# keyword [C++]
ms.assetid: a5902cf8-a14d-4559-aefb-c178615d45bb
ms.openlocfilehash: ffdf9a8b11912bde38e15408228670c8cff9a503
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188318"
---
# <a name="interoperability-with-other-net-languages-ccli"></a>與其他 .NET 程式設計語言間的互通性 (C++/CLI)

在本節中的主題示範如何建立視覺效果中的組件C++，從取用或提供功能給撰寫的組件C#或 Visual Basic。

## <a name="consume_indexer"></a> 使用 C# 索引子

視覺化C++不包含索引子;它有索引的屬性。 若要使用 C# 索引子，存取索引子，如同它是索引的屬性。

如需索引子的詳細資訊，請參閱：

- [索引子](/dotnet/csharp/programming-guide/indexers/index)

### <a name="example"></a>範例

下列 C# 程式會定義索引子。

```csharp
// consume_cs_indexers.cs
// compile with: /target:library
using System;
public class IndexerClass {
   private int [] myArray = new int[100];
   public int this [int index] {   // Indexer declaration
      get {
         // Check the index limits.
         if (index < 0 || index >= 100)
            return 0;
         else
            return myArray[index];
      }
      set {
         if (!(index < 0 || index >= 100))
            myArray[index] = value;
      }
   }
}
/*
// code to consume the indexer
public class MainClass {
   public static void Main() {
      IndexerClass b = new IndexerClass();

      // Call indexer to initialize elements 3 and 5
      b[3] = 256;
      b[5] = 1024;
      for (int i = 0 ; i <= 10 ; i++)
         Console.WriteLine("Element #{0} = {1}", i, b[i]);
   }
}
*/
```

### <a name="example"></a>範例

此視覺效果C++程式會使用索引子。

```cpp
// consume_cs_indexers_2.cpp
// compile with: /clr
#using "consume_cs_indexers.dll"
using namespace System;

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->default[0] = 21;
   for (int i = 0 ; i <= 10 ; i++)
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);
}
```

```Output
Element #0 = 21
Element #1 = 0
Element #2 = 0
Element #3 = 0
Element #4 = 0
Element #5 = 0
Element #6 = 0
Element #7 = 0
Element #8 = 0
Element #9 = 0
Element #10 = 0
```

## <a name="implement_isas"></a> 實作 is 和 as C# 關鍵字

本主題說明如何實作的功能`is`並`as`C#視覺效果中的關鍵字C++。

### <a name="example"></a>範例

```cpp
// CS_is_as.cpp
// compile with: /clr
using namespace System;

interface class I {
public:
   void F();
};

ref struct C : public I {
   virtual void F( void ) { }
};

template < class T, class U >
Boolean isinst(U u) {
   return dynamic_cast< T >(u) != nullptr;
}

int main() {
   C ^ c = gcnew C();
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)

   // simulate 'as':
   Object ^ o = "f";
   if ( isinst< String ^ >(o) )
      Console::WriteLine("o is a string");
}
```

```Output
o is a string
```

## <a name="implement_locak"></a> 實作鎖定 C# 關鍵字

本主題說明如何實作C#`lock`視覺效果中的關鍵字C++。

您也可以使用`lock`類別中C++支援程式庫。 請參閱[同步處理 (lock 類別)](../dotnet/synchronization-lock-class.md)如需詳細資訊。

### <a name="example"></a>範例

```cpp
// CS_lock_in_CPP.cpp
// compile with: /clr
using namespace System::Threading;
ref class Lock {
   Object^ m_pObject;
public:
   Lock( Object ^ pObject ) : m_pObject( pObject ) {
      Monitor::Enter( m_pObject );
   }
   ~Lock() {
      Monitor::Exit( m_pObject );
   }
};

ref struct LockHelper {
   void DoSomething();
};

void LockHelper::DoSomething() {
   // Note: Reference type with stack allocation semantics to provide
   // deterministic finalization

   Lock lock( this );
   // LockHelper instance is locked
}

int main()
{
   LockHelper lockHelper;
   lockHelper.DoSomething();
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
