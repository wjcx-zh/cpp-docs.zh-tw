---
title: 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs:
- C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47b9fd580d1ebabf4352104fe49f1d3c982a49e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="message"></a>訊息
傳送字串常值至標準輸出，而不終止編譯。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>備註  
 典型用法**訊息**pragma 會在編譯時期顯示告知性訊息。  
  
 *Messagestring*參數可以是巨集展開為字串常值，而您可以串連此類巨集與任意組合的字串常值。  
  
 如果您使用中的預先定義巨集**訊息**pragma 巨集應該傳回一個字串，否則您就必須將巨集的輸出轉換為字串。  
  
 下列程式碼片段使用**訊息**pragma 在編譯期間顯示訊息：  
  
```  
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
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)