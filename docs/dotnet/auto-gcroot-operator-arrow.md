---
title: auto_gcroot::operator-&gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_gcroot.operator->
- msclr::auto_gcroot::operator->
- auto_gcroot::operator->
- msclr.auto_gcroot.operator->
helpviewer_keywords:
- operator->
ms.assetid: 2c77bc53-5f77-4544-9485-c950cd8e0bb1
ms.openlocfilehash: c4ec96127ad595b399412b13600e6f9d4970e9fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566461"
---
# <a name="autogcrootoperator-gt"></a>auto_gcroot::operator-&gt;

成員存取運算子。

## <a name="syntax"></a>語法

```
_element_type operator->() const;
```

## <a name="return-value"></a>傳回值

所包裝的物件`auto_gcroot`。

## <a name="example"></a>範例

```
// msl_auto_gcroot_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }

   int m_i;
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_gcroot.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_gcroot 成員](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::get](../dotnet/auto-gcroot-get.md)