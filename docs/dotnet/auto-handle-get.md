---
title: auto_handle::get
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_handle::get
- msclr::auto_handle::get
- auto_handle.get
- msclr.auto_handle.get
helpviewer_keywords:
- auto_handle::get
ms.assetid: 8c75727b-8f21-44b3-be3e-7eb8858da4f7
ms.openlocfilehash: f5c5d7646cfae20c66e109c7aca9f2cb8d5ff8cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528930"
---
# <a name="autohandleget"></a>auto_handle::get

取得包含的物件。

## <a name="syntax"></a>語法

```
_element_type ^ get();
```

## <a name="return-value"></a>傳回值

包含的物件。

## <a name="example"></a>範例

```
// msl_auto_handle_get.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

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
   auto_handle<ClassA> a = gcnew ClassA( "first" );
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

**標頭檔** \<msclr\auto_handle.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_handle 成員](../dotnet/auto-handle-members.md)