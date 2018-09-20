---
title: 最後 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 818ee6736d51303b047cb5a47aae02441557db29
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447273"
---
# <a name="finally"></a>finally

除了`try`並`catch`子句，CLR 例外狀況處理支援`finally`子句。 語意都完全相同`__finally`封鎖中處理 (SEH) 的結構化例外狀況。 A`__finally`區塊可以接`try`或`catch`區塊。

## <a name="remarks"></a>備註

目的`finally`區塊是清理之後發生的例外狀況留下任何資源。 請注意，`finally`區塊永遠會執行，即使擲回任何例外狀況。 `catch`擲回 managed 例外狀況時，才會執行區塊內相關聯`try`區塊。

`finally` 是內容相關性的關鍵字;請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)如需詳細資訊。

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

[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)