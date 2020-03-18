---
title: 使用 __declspec(dllimport) 匯入函式呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442515"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>使用 __declspec(dllimport) 匯入函式呼叫

下列程式碼範例示範如何使用 **_declspec （dllimport）** 將 DLL 中的函式呼叫匯入至應用程式。 假設 `func1` 是位於 DLL 中的函式，與包含**main**函式的 .exe 檔案不同。

若沒有 **__declspec （dllimport）** ，請指定此程式碼：

```
int main(void)
{
   func1();
}
```

編譯器會產生如下所示的程式碼：

```
call func1
```

而且連結器會將呼叫轉譯成如下所示的內容：

```
call 0x4000000         ; The address of 'func1'.
```

如果 `func1` 存在於另一個 DLL 中，連結器就無法直接解決此問題，因為它無法得知 `func1` 的位址為何。 在16位的環境中，連結器會將此程式碼位址加入 .exe 檔案中的清單，在執行時間會使用正確的位址來進行修補。 在32位和64位的環境中，連結器會產生它知道位址的 Thunk。 在32位環境中，Thunk 看起來像這樣：

```
0x40000000:    jmp DWORD PTR __imp_func1
```

這裡 `imp_func1` 是 .exe 檔案的匯入位址表格中 `func1` 位置的位址。 因此，連結器知道所有的位址。 載入器只需要在載入時更新 .exe 檔案的匯入位址表，讓所有專案都能正常運作。

因此，使用 **__declspec （dllimport）** 是較好的方式，因為連結器不會產生 Thunk （如果不需要的話）。 Thunk 會使程式碼更大（在 RISC 系統上，它可以有數個指示），而且可能會降低您的快取效能。 如果您告訴編譯器函式是在 DLL 中，它可以為您產生間接呼叫。

現在這段程式碼：

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

產生此指令：

```
call DWORD PTR __imp_func1
```

沒有 Thunk，而且沒有 `jmp` 的指示，因此程式碼較小且更快速。

另一方面，對於 DLL 內的函式呼叫，您不想要使用間接呼叫。 您已經知道函式的位址。 因為需要在間接呼叫之前載入和儲存函式位址的時間和空間，所以直接呼叫的速度一律會更快且更小。 當您從 DLL 本身外部呼叫 DLL 函式時，您只想要使用 **__declspec （dllimport）** 。 建立 DLL 時，請勿在 DLL 內的函式上使用 **__declspec （dllimport）** 。

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
