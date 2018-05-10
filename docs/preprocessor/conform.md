---
title: 符合 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b145225cfed3131b406d15827b589aed718d16bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="conform"></a>conform
**C + + 特定的**  
  
 指定的執行階段行為[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 指定要修改的編譯器選項名稱。 唯一有效*名稱*是`forScope`。  
  
 **顯示**（選擇性）  
 會導致目前的設定*名稱*（true 或 false） 在編譯期間透過警告訊息會顯示。 例如，`#pragma conform(forScope, show)`。  
  
 **開、 關**（選擇性）  
 設定*名稱*至**上**啟用[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。 預設值是**關閉**。  
  
 **推入**（選擇性）  
 推播通知的目前值*名稱*至內部編譯器堆疊。 如果您指定*識別碼*，您可以指定**上**或**關閉**值*名稱*推入堆疊。 例如，`#pragma conform(forScope, push, myname, on)`。  
  
 **pop** （選擇性）  
 設定的值*名稱*頂端的內部編譯器堆疊，然後從堆疊中推出的值。 如果您指定的識別項**pop**，將會推出堆疊，直到它找到的記錄*識別碼*，這也會從; 目前的值*名稱*中在堆疊上的下一個記錄會變成新值*名稱*。 如果您指定要推出*識別碼*不在堆疊上的記錄**pop**會被忽略。  
  
 *識別項*（選擇性）  
 可能包含在**發送**或**pop**命令。 如果*識別碼*使用時，則**上**或**關閉**規範也可以使用。  
  
## <a name="example"></a>範例  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)