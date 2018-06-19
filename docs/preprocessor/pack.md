---
title: 組件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs:
- C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c29c31cae2b7de59d4db5ed6546ad4eda6baecf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843622"
---
# <a name="pack"></a>pack
指定結構、等位及類別成員的封裝對齊。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>備註  
 封裝類別是指將類別的成員交錯放入記憶體中，這可能表示部分或所有的成員能夠在比目標架構的預設對齊還小的界限上對齊。 `pack` 在資料宣告層級提供控制項。 這不同於編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md)，後者只會提供模組層級的控制項。 `pack` 函式會在第一個 `struct`、`union` 或在出現 pragma 之後的 `class` 宣告中生效。 `pack` 對定義無作用。 呼叫`pack`沒有引數集`n`編譯器選項所設定的值 **/Zp**。 如果未設定編譯器選項，則預設值為 8。  
  
 如果您變更結構的對齊，結構在記憶體中可能不會佔用太多空間，但效能可能會降低，甚至可能會出現硬體所產生的未對齊存取例外狀況。  您可以使用，以修改此例外狀況行為[SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621)。  
  
 **顯示**（選擇性）  
 會顯示封裝對齊目前的位元組值。 此值是透過警告訊息顯示。  
  
 **推入**（選擇性）  
 會推送內部編譯器堆疊目前的封裝對齊值，並且將目前的封裝對齊值設為 `n`。 如果未指定 `n`，會推送目前的封裝對齊值。  
  
 **pop** （選擇性）  
 會從內部編譯器堆疊頂端移除記錄。 如果`n`中未指定**pop**，則產生的記錄在堆疊的頂端與相關聯的封裝值即為新封裝對齊值。 如果指定 `n` (例如 `#pragma pack(pop, 16)`)，`n` 會成為新的封裝對齊值。 如果您使用 `identifier` (例如 `#pragma pack(pop, r1)`) 快顯，則會快顯堆疊上的所有記錄，直到找到具有 `identifier` 的記錄為止。 會快顯該記錄，且與堆疊頂端產生的記錄關聯的封裝值即為新的封裝對齊值。 如果快顯`identifier`，找不到任何記錄在堆疊上，則**pop**會被忽略。  
  
 `identifier` (選擇性)  
 當搭配**發送**，會指派名稱給內部編譯器堆疊的記錄。 當搭配**pop**，會將記錄在內部堆疊，直到`identifier`已移除; 如果`identifier`找不到在內部堆疊，不會推出。  
  
 `n` (選擇性)  
 以位元組為單位指定要用於封裝的值。 如果編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md)個模組的預設值未設定`n`為 8。 有效值為 1、2、4、8 和 16。 成員會在界限對齊，此界限可能是 `n` 的倍數，也可能是成員大小的倍數，以其中較小者為準。  
  
 `#pragma pack(pop, identifier, n)` 未定義。  
  
 如需有關如何修改對齊的詳細資訊，請參閱下列主題：  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md)(x64 專用)  
  
    > [!WARNING]
    >  請注意，在 Visual Studio 2015 和更新版本中，您可以使用標準 alignas 和 alignof 運算子，與可跨編譯器移植的 `__alignof` 和 `declspec( align )` 不同。 C++ 標準無法處理封裝作業，因此您仍須使用 `pack` (或其他編譯器上的對應延伸模組) 來指定比目標架構的文字大小還小的對齊。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `pack` pragma 變更結構的對齊方式。  
  
```  
// pragma_directives_pack.cpp  
#include <stddef.h>  
#include <stdio.h>  
  
struct S {  
   int i;   // size 4  
   short j;   // size 2  
   double k;   // size 8  
};  
  
#pragma pack(2)  
struct T {  
   int i;  
   short j;  
   double k;  
};  
  
int main() {  
   printf("%zu ", offsetof(S, i));  
   printf("%zu ", offsetof(S, j));  
   printf("%zu\n", offsetof(S, k));  
  
   printf("%zu ", offsetof(T, i));  
   printf("%zu ", offsetof(T, j));  
   printf("%zu\n", offsetof(T, k));  
}  
```  
  
```  
0 4 8  
0 4 6  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用**發送**， **pop**，和**顯示**語法。  
  
```  
// pragma_directives_pack_2.cpp  
// compile with: /W1 /c  
#pragma pack()   // n defaults to 8; equivalent to /Zp8  
#pragma pack(show)   // C4810  
#pragma pack(4)   // n = 4  
#pragma pack(show)   // C4810  
#pragma pack(push, r1, 16)   // n = 16, pushed to stack  
#pragma pack(show)   // C4810  
#pragma pack(pop, r1, 2)   // n = 2 , stack popped  
#pragma pack(show)   // C4810  
```  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)