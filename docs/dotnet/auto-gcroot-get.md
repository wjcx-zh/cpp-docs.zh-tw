---
title: auto_gcroot::get
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::get
- msclr.auto_gcroot.get
- auto_gcroot::get
- auto_gcroot.get
helpviewer_keywords:
- auto_gcroot::get
ms.assetid: 0e922019-1cf5-4220-b5ab-6c4a2a6b40ec
ms.openlocfilehash: 0759e8b08f12ae12c9960b8fed431145502851fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565129"
---
# <a name="autogcrootget"></a>auto_gcroot::get

取得包含的物件。

## <a name="syntax"></a>語法

```cpp
_element_type get() const;
```

## <a name="return-value"></a>傳回值

包含的物件。

## <a name="example"></a>範例

```cpp
// msl_auto_gcroot_get.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ){
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

void PrintA( ClassA^ a ) {
   a->PrintHello();
}

int main() {
   auto_gcroot<ClassA^> a = gcnew ClassA( "first" );
   a->PrintHello();

   ClassA^ a2 = a.get();
   a2->PrintHello();

   PrintA( a.get() );
}
```

```Output
in ClassA constructor:first
Hello from first A!
Hello from first A!
Hello from first A!
in ClassA destructor:first
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_gcroot.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_gcroot 成員](../dotnet/auto-gcroot-members.md)