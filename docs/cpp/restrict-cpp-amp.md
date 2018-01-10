---
title: "限制 (c + + AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs: C++
helpviewer_keywords: restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60ac40e2cb64c307574d14c1f7cc7a5290c740ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)
限制規範可以套用到函式和 Lambda 宣告。 它會在函式中的程式碼上強制執行限制，以及在使用 C++ Accelerated Massive Parallelism (C++ AMP) 的應用程式中函式的行為上強制執行限制。  
  
> [!NOTE]
>  如需有關資訊`restrict`關鍵字屬於`__declspec`儲存類別屬性，請參閱[限制](../cpp/restrict.md)。  
  
 `restrict` 子句的格式如下：  
  
|子句|描述|  
|------------|-----------------|  
|`restrict(cpu)`|函式可以使用完整的 C++ 語言。 只有使用 restrict(cpu) 函式宣告的其他函式可以呼叫函式。|  
|`restrict(amp)`|函式只能使用 C++ AMP 可以加速之 C++ 語言的子集。|  
|`restrict(cpu)` 和 `restrict(amp)` 的序列。|函式必須同時符合 `restrict(cpu)` 和 `restrict(amp)` 的限制。 函式可由使用 `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)` 或 `restrict(amp, cpu)` 宣告的函式呼叫。<br /><br /> `restrict(A) restrict(B)` 格式可以撰寫為 `restrict(A,B)`。|  
  
## <a name="remarks"></a>備註  
 `restrict` 關鍵字是內容關鍵字。 限制規範、`cpu` 和 `amp` 不是保留字。 規範的清單無法擴充。 未內含 `restrict` 子句的函式與內含 `restrict(cpu)` 子句的函式。  
  
 內含 `restrict(amp)` 子句的函式具有下列限制：  
  
-   函式只會呼叫內含 `restrict(amp)` 子句的函式。  
  
-   函式必須為可內嵌。  
  
-   函式可以只宣告 `int`、`unsigned int`、`float` 和 `double` 變數，以及只內含這些類型的類別和結構。 如果是在複合類型中使用，則也可以使用 `bool`，不過必須對齊 4 位元組。  
  
-   Lambda 函式無法透過參考方式擷取，也無法擷取指標。  
  
-   參考和單一間接取值指標只支援區域變數、函式引數和傳回型別。  
  
-   不允許使用下列各項：  
  
    -   遞迴。  
  
    -   以宣告的變數[volatile](../cpp/volatile-cpp.md)關鍵字。  
  
    -   虛擬函式。  
  
    -   函式的指標。  
  
    -   成員函式的指標。  
  
    -   結構中的指標。  
  
    -   指標的指標。  
  
    -   `goto` 陳述式。  
  
    -   標記陳述式。  
  
    -   `try`、`catch` 或 `throw` 陳述式。  
  
    -   全域變數。  
  
    -   靜態變數。 使用[tile_static 關鍵字](../cpp/tile-static-keyword.md)改為。  
  
    -   `dynamic_cast` 轉換。  
  
    -   `typeid` 運算子。  
  
    -   asm 宣告。  
  
    -   Varargs。  
  
 如需函式限制的討論，請參閱[restrict （amp) 限制](http://go.microsoft.com/fwlink/p/?LinkId=251089)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`restrict(amp)`子句。  
  
```  
  
void functionAmp() restrict(amp) {}   
void functionNonAmp() {}   
  
void callFunctions() restrict(amp)   
{   
    // int is allowed.  
    int x;  
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.  
    // long long int y;   
  
    // Calling an amp-restricted function is allowed.  
    functionAmp();   
  
    // Calling a non-amp-restricted function is not allowed.  
    // functionNonAmp();   
  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)