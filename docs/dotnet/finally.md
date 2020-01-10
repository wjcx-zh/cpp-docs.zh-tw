---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988341"
---
# <a name="finally"></a>finally

除了 `try` 和 `catch` 子句之外，CLR 例外狀況處理也支援 `finally` 子句。 此語義與結構化例外狀況處理（SEH）中的 `__finally` 區塊相同。 `__finally` 區塊可以跟隨 `try` 或 `catch` 區塊。

## <a name="remarks"></a>備註

`finally` 區塊的目的是要清除例外狀況發生後剩餘的任何資源。 請注意，即使沒有擲回例外狀況，也一定會執行 `finally` 區塊。 只有在相關聯的 `try` 區塊內擲回 managed 例外狀況時，才會執行 `catch` 區塊。

`finally` 是內容相關的關鍵字;如需詳細資訊，請參閱[內容相關關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例示範簡單的 `finally` 區塊：

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

## <a name="see-also"></a>請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)
