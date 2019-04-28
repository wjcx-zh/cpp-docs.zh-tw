---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: f7db4320cf901412e3a9e3de682d0cfbcc9f23bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223010"
---
# <a name="finally"></a>finally

除了`try`並`catch`子句，CLR 例外狀況處理支援`finally`子句。 語意都完全相同`__finally`封鎖中處理 (SEH) 的結構化例外狀況。 A`__finally`區塊可以接`try`或`catch`區塊。

## <a name="remarks"></a>備註

目的`finally`區塊是清理之後發生的例外狀況留下任何資源。 請注意，`finally`區塊永遠會執行，即使擲回任何例外狀況。 `catch`擲回 managed 例外狀況時，才會執行區塊內相關聯`try`區塊。

`finally` 是內容相關性的關鍵字;請參閱[即時線上關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例示範簡單`finally`區塊：

```
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
