---
title: 編譯器警告（層級4） C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 0e5bdab6ff0d0508abaf5f726d1356102cfca04a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219972"
---
# <a name="compiler-warning-level-4-c4121"></a>編譯器警告（層級4） C4121

'symbol' : 成員的記憶體對齊受 pack 影響

編譯器加入了填補來調整封裝邊界上的結構成員，但是封裝值小於成員的大小。 例如，下列程式碼片段會產生 C4121：

```cpp
// C4121.cpp
// compile with: /W4 /c
#pragma pack(2)
struct s
{
   char a;
   int b; // C4121
   long long c;
};
```

若要修正這個問題，請進行下列任一項變更：

- 將封裝大小變更為造成警告的成員大小，或更大的大小。 例如，在這個程式碼片段中，將 `pack(2)` 變更為 `pack(4)` 或 `pack(8)`。

- 依從最大到最小的順序，重新排列成員宣告。 在程式碼片段中，將結構成員的順序反轉，讓 **`long long`** 成員在之前 **`int`** ，和在 **`int`** 之前 **`char`** 。

只有在編譯器於資料成員前面加入填補時，才會出現這個警告。 當封裝將資料放入未對齊資料類型的記憶體位置，而資料成員前面沒有填補時，並不會出現這個警告。 當資料未在大小為資料的數倍之邊界上對齊時，效能就可能會降低。 讀取和寫入未對齊的資料會造成某些架構上發生處理器錯誤，而錯誤可能需要花兩、三倍以上的時間才能解決。 未對齊的資料存取無法移植到某些 RISC 架構中。

您可以使用[#pragma pack](../../preprocessor/pack.md)或[/Zp](../../build/reference/zp-struct-member-alignment.md)來指定結構對齊方式。 （當指定 **/Zp1**時，編譯器不會產生這個警告）。
