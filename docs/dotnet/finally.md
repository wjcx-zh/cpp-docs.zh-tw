---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: b3331c17fc2313cbd6146db3beb015cd8d8c1eeb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221454"
---
# <a name="finally"></a>finally

除了 **`try`** 和子句之外 **`catch`** ，CLR 例外狀況處理也支援 **`finally`** 子句。 此語義與 **`__finally`** 結構化例外狀況處理（SEH）中的區塊相同。 **`__finally`** 區塊可以在 **`try`** 或區塊之後 **`catch`** 。

## <a name="remarks"></a>備註

區塊的目的 **`finally`** 是要清除例外狀況發生後剩餘的任何資源。 請注意， **`finally`** 即使沒有擲回例外狀況，也一定會執行區塊。 **`catch`** 只有在相關聯的區塊內擲回 managed 例外狀況時，才會執行區塊 **`try`** 。

`finally`是內容相關的關鍵字;如需詳細資訊，請參閱[內容相關關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例示範簡單的 **`finally`** 區塊：

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>另請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)
