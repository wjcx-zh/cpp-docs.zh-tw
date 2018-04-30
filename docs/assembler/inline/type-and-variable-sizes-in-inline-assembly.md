---
title: 類型和變數大小，在內嵌組譯碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- length
- Type
dev_langs:
- C++
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3466158c507e618e701df5aed35db7e5814abe52
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>內嵌組譯碼中的類型和變數大小
**Microsoft 特定的**  
  
 **長度**，**大小**，和**類型**運算子在內嵌組譯碼中具有受限的意義。 這些運算子完全無法搭配 `DUP` 運算子使用 (因為您無法使用 MASM 指示詞或運算子定義資料)。 但是，您可以使用這些運算子尋找 C 或 C++ 變數或類型的大小：  
  
-   **長度**運算子可以傳回陣列中的項目數目。 它會針對非陣列變數傳回數值 1。  
  
-   **大小**運算子可以傳回 C 或 c + + 變數的大小。 變數的大小是其**長度**和**類型**。  
  
-   **類型**運算子可以傳回 C 或 c + + 類型或變數的大小。 如果變數是陣列、**類型**傳回陣列中單一項目的大小。  
  
 例如，如果您的程式擁有 8 個元素的 `int` 陣列，  
  
```  
int arr[8];  
```  
  
 下列 C 和組譯碼運算式會產生 `arr` 及其元素的大小。  
  
|__asm|C|大小|  
|-------------|-------|----------|  
|**長度**arr|`sizeof`(arr)/`sizeof`(arr[0])|8|  
|**大小**arr|`sizeof`(arr)|32|  
|**型別**arr|`sizeof`(arr[0])|4|  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)