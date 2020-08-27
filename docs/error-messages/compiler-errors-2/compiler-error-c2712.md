---
title: 編譯器錯誤 C2712
description: 描述 Microsoft C/c + + 編譯器錯誤 C2712。
ms.date: 08/25/2020
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 2f0b883607241473a429919e06de9e975fa2e3c1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898701"
---
# <a name="compiler-error-c2712"></a>編譯器錯誤 C2712

> `__try`在需要物件回溯的函式中無法使用

## <a name="remarks"></a>備註

如果您使用，就可能會發生錯誤 C2712 [`/EHsc`](../../build/reference/eh-exception-handling-model.md) ，而且具有結構化例外狀況處理的函式也有需要回溯 (終結) 的物件。

可能的解決方案：

- 將需要 SEH 的程式碼移至另一個函式

- 重寫使用 SEH 的函式，以避免使用具有解構函式的本機變數和參數。 請勿在建構函式或解構函式中使用 SEH

- 編譯時不要使用 /EHsc

如果您呼叫使用關鍵字所宣告的方法，也可能會發生錯誤 C2712 [`__event`](../../cpp/event.md) 。 由於事件可能會用在多執行緒環境中，因此編譯器會產生程式碼以防止基礎事件物件的操作，然後將產生的程式碼括在 SEH [ `try-finally` 語句](../../cpp/try-finally-statement.md)中。 因此，如果您呼叫事件方法，並以類型具有解構函式的引數傳值，就會發生錯誤 C2712。 此情況下的解決方案之一，是傳遞引數做為常數參考。

如果您使用進行編譯 **`/clr:pure`** ，並在區塊中宣告指向函式的靜態陣列，也可能會發生 C2712 **`__try`** 。 靜態成員需要編譯器在下使用動態初始化 **`/clr:pure`** ，這表示 c + + 例外狀況處理。 不過，區塊中不允許 c + + 例外狀況處理 **`__try`** 。

**`/clr:pure`** 和 **`/clr:safe`** 編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

## <a name="example"></a>範例

下列範例會產生 C2712，並說明如何加以修正。

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
