---
title: 匯入函式呼叫使用 __declspec （dllimport） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1239ee3b33a9d6c8443161bacae6daea20260c1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="importing-function-calls-using-declspecdllimport"></a>使用 __declspec(dllimport) 匯入函式呼叫
下列程式碼範例示範如何使用 **_declspec(dllimport)** 從 DLL 匯入函式呼叫，為應用程式。 假設`func1`是位於與.exe 檔案，其中包含不同的 DLL 函式**主要**函式。  
  
 不含 **__declspec （dllimport)**，假設此程式碼：  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 編譯器會產生程式碼看起來像這樣：  
  
```  
call func1  
```  
  
 和連結器會轉譯在呼叫結果類似這樣：  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 如果`func1`存在於另一個 DLL，此連結器無法解析此直接，因為它有無從得知哪些位址`func1`是。 在 16 位元環境中，連結器會將這個程式碼位址加入至清單中，載入器會在執行階段使用正確的位址修補程式的.exe 檔案。 在 32 位元和 64 位元環境中，連結器產生的 thunk，其中它確實知道位址。 在 32 位元環境中的 thunk 看起來像：  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 這裡`imp_func1`的位址`func1`.exe 檔的匯入位址表中的位置。 連結器因此已知的所有地址。 載入器只需要更新的.exe 檔案的匯入位址表在載入時間，才能正確運作的所有項目。  
  
 因此，使用 **__declspec （dllimport)** 較佳，因為如果不需要連結器不會產生 thunk。 較大的 thunk 讓程式碼 （RISC 在系統上，它可以是數個指示），可能會降低快取效能。 如果您會告訴編譯器函式是在 DLL 中，它可為您產生間接呼叫。  
  
 因此，現在此程式碼：  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 會產生此指示：  
  
```  
call DWORD PTR __imp_func1  
```  
  
 沒有任何 thunk，且沒有`jmp`指令，因此程式碼是較小且更快速。  
  
 相反地，於 DLL 內的函式呼叫，您不要使用間接呼叫。 您已經知道函式的位址。 因為時間和空間需要載入和儲存在間接呼叫之前函式的位址，直接呼叫會較快與規模較小。 您只想要使用 **__declspec （dllimport)** 時呼叫 DLL 函式從該 DLL 本身之外。 請勿使用 **__declspec （dllimport)** 函式內的 DLL 建立 DLL 時。  
  
## <a name="see-also"></a>另請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)