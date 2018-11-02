---
title: 使用 __declspec(dllimport) 匯入函式呼叫
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 513e6bd7b1120dd710852ab61aa7603bba74907e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498224"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>使用 __declspec(dllimport) 匯入函式呼叫

下列程式碼範例示範如何使用 **_declspec(dllimport)** 函式呼叫從 DLL 匯應用程式。 假設`func1`是位於與.exe 檔案，其中包含不同的 DLL 函式**主要**函式。

不含 **__declspec （dllimport)**，此程式碼：

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

然後，連結器會轉譯成類似下面的呼叫：

```
call 0x4000000         ; The address of 'func1'.
```

如果`func1`存在於另一個 DLL 時，此連結器不能直接解析，因為它有沒有辦法知道哪些位址`func1`是。 在 16 位元環境中，連結器會將這個程式碼位址加入至清單中的.exe 檔案，載入器會在執行階段使用的正確位址修補。 在 32 位元和 64 位元環境中，連結器會產生的 thunk，它都知道位址。 在 32 位元環境中的 thunk，看起來像：

```
0x40000000:    jmp DWORD PTR __imp_func1
```

以下`imp_func1`的位址`func1`匯入位址表的.exe 檔案中的位置。 連結器因此已知的所有地址。 載入器只有在 for 一切正常運作的載入時間更新的.exe 檔案的匯入位址表格。

因此，使用 **__declspec （dllimport)** 是更好的因為連結器不會產生 thunk，如果您不需要。 較大的 thunk 讓程式碼 （RISC 在系統上，它可以是數個指令），可能會降低您的快取效能。 如果您告訴編譯器函式是在 DLL 中，它可以為您產生的間接呼叫。

因此，現在此程式碼：

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

會產生這個指示：

```
call DWORD PTR __imp_func1
```

沒有任何 thunk，但沒有`jmp`指令，因此程式碼是較小且更快速。

相反地，於 DLL 內的函式呼叫，不想要使用的間接呼叫。 您已經知道函式的位址。 因為時間和空間才能載入和儲存之前的間接呼叫函式的位址，直接呼叫總是更快更小。 您只想要 **__declspec （dllimport)** 呼叫 DLL 函式從外部 DLL 本身時。 請勿使用 **__declspec （dllimport)** 上建立該 DLL 時的 DLL 內的函式。

## <a name="see-also"></a>另請參閱

[匯入至應用程式](../build/importing-into-an-application.md)