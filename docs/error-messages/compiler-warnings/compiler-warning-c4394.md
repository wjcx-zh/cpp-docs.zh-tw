---
title: 編譯器警告 C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: ad6b9624a1bf510465843167d104d1bec189bc70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197354"
---
# <a name="compiler-warning-c4394"></a>編譯器警告 C4394

' function '：每個 appdomain 的符號不應以 __declspec （dllexport）標記

以[appdomain](../../cpp/appdomain.md)修飾詞標記的函式 **`__declspec`** 會編譯為 MSIL （非原生），而且 managed 函數不支援匯出資料表（[匯出](../../windows/export.md) **`__declspec`** 修飾詞）。

您可以宣告 Managed 函式具有公用的存取範圍。 如需詳細資訊，請參閱[類型可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成員可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。

C4394 一律會發出為錯誤。  您可以使用或/wd 關閉此警告 `#pragma warning` ; **/wd**如需詳細資訊，請參閱[warning](../../preprocessor/warning.md)或[/W、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/WE、/Wo、/Wv、/wx （警告層級）](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>範例

下列範例會產生 C4394。

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
