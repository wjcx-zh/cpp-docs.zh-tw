---
title: message pragma
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 48605fbef3b6d81c140e663e950429cd3dcf9b19
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218803"
---
# <a name="message-pragma"></a>message pragma

傳送字串常值至標準輸出，而不終止編譯。

## <a name="syntax"></a>語法

> **#pragma 訊息 (** *訊息字串* **)**

## <a name="remarks"></a>備註

**訊息**pragma 的一般用法是在編譯時期顯示參考用訊息。

*訊息字串*參數可以是展開為字串常值的宏, 而您可以將此類宏與任意組合的字串常值串連。

如果您在**message** pragma 中使用預先定義的宏, 則宏應該會傳回字串。 否則, 您必須將宏的輸出轉換成字串。

下列程式碼片段會使用**message** pragma 在編譯期間顯示訊息:

```cpp
// pragma_directives_message1.cpp
// compile with: /LD
#if _M_IX86 >= 500
#pragma message("_M_IX86 >= 500")
#endif

#pragma message("")

#pragma message( "Compiling " __FILE__ )
#pragma message( "Last modified on " __TIMESTAMP__ )

#pragma message("")

// with line number
#define STRING2(x) #x
#define STRING(x) STRING2(x)

#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")

#pragma message("")
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
