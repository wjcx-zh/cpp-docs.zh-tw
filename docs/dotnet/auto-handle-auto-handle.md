---
title: auto_handle::auto_handle |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle::auto_handle
- msclr.auto_handle.auto_handle
- auto_handle.auto_handle
- msclr::auto_handle::auto_handle
dev_langs:
- C++
helpviewer_keywords:
- auto_handle method
ms.assetid: 0b68ab31-023c-4224-9601-9231412c4e13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a3879005147235db3193d1d63cb69d7eb789cace
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415092"
---
# <a name="autohandleautohandle"></a>auto_handle::auto_handle

`auto_handle`建構函式。

## <a name="syntax"></a>語法

```
auto_handle();
auto_handle(
   _element_type ^ _ptr
);
auto_handle(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle(
   auto_handle<_other_type> % _right
);
```

#### <a name="parameters"></a>參數

*_ptr*<br/>
要自己的物件。

*右方 （_r)*<br/>
現有的 `auto_handle`。

## <a name="example"></a>範例

```
// msl_auto_handle_auto_handle.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;
ref class RefClassA {
protected:
   String^ m_s;
public:
   RefClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in RefClassA constructor: " + m_s );
   }
   ~RefClassA() {
      Console::WriteLine( "in RefClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class RefClassB : RefClassA {
public:
   RefClassB( String^ s ) : RefClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   {
      auto_handle<RefClassA> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_handle<RefClassB> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_handle<RefClassA> a(b); //construct from derived type
      a->PrintHello();
      auto_handle<RefClassA> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: first
Hello from first A!
in RefClassA destructor: first
in RefClassA constructor: second
Hello from second B!
Hello from second A!
Hello from second A!
in RefClassA destructor: second
done
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_handle.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_handle 成員](../dotnet/auto-handle-members.md)<br/>
[auto_handle::operator=](../dotnet/auto-handle-operator-assign.md)<br/>
[auto_handle::~auto_handle](../dotnet/auto-handle-tilde-auto-handle.md)