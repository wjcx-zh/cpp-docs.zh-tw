---
title: 使用 __declspec(dllimport) 匯入函式呼叫
description: 呼叫 DLL 資料和函數時，使用 __declspec （dllimport）的方式和原因。
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765717"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>使用匯入函式呼叫`__declspec(dllimport)`

使用來標注呼叫**`__declspec(dllimport)`** 會使其更快。 **`__declspec(dllimport)`** 一律需要存取匯出的 DLL 資料。

## <a name="import-a-function-from-a-dll"></a>從 DLL 匯入函式

下列程式碼範例示範如何使用**`__declspec(dllimport)`** ，將 DLL 中的函式呼叫匯入應用程式。 假設`func1`是 DLL 中的函式，與包含**main**函式的可執行檔分開。

若**`__declspec(dllimport)`** 沒有，請指定此程式碼：

```C
int main(void)
{
   func1();
}
```

編譯器會產生如下所示的程式碼：

```asm
call func1
```

而且連結器會將呼叫轉譯成如下所示的內容：

```asm
call 0x4000000         ; The address of 'func1'.
```

如果`func1`存在於另一個 DLL 中，連結器就無法直接解析此位址，因為它無法得知的位址`func1`為何。 在32位和64位的環境中，連結器會在已知的位址產生 Thunk。 在32位環境中，Thunk 看起來像這樣：

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

以下`__imp_func1`是可執行檔的`func1`匯入位址表格中的位置位址。 連結器知道所有這些位址。 載入器只需要在載入時更新可執行檔的匯入位址表，所有專案才能正常運作。

這就是為什麼**`__declspec(dllimport)`** 使用更好：因為連結器不會產生 Thunk （如果不需要的話）。 Thunk 會使程式碼更大（在 RISC 系統上，它可以有數個指示），而且可能會降低您的快取效能。 如果您告訴編譯器函式是在 DLL 中，它可以為您產生間接呼叫。

現在這段程式碼：

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

產生此指令：

```asm
call DWORD PTR __imp_func1
```

沒有 Thunk 和`jmp`指令，因此程式碼較小且更快速。 您也可以在不使用整個程式**`__declspec(dllimport)`** 優化的情況下取得相同的效果。 如需詳細資訊，請參閱 [/GL (整個程式最佳化)](reference/gl-whole-program-optimization.md)。

對於 DLL 內的函式呼叫，您不想要使用間接呼叫。 連結器已知道函式的位址。 在間接呼叫之前，需要額外的時間和空間來載入和儲存函式的位址。 直接呼叫一律會更快且更小。 您只想要在**`__declspec(dllimport)`** 從 dll 本身外部呼叫 dll 函式時使用。 建立 DLL **`__declspec(dllimport)`** 時，請勿在 dll 內的函式上使用。

## <a name="see-also"></a>請參閱

[匯入至應用程式](importing-into-an-application.md)
