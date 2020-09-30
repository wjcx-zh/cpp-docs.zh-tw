---
title: 編譯器警告 C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: fc4d66444b4ddc5c855e88d466ccc2f42c60e0ca
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510057"
---
# <a name="compiler-warning-c4394"></a>編譯器警告 C4394

' function '：個別 appdomain 符號不應標記為 __declspec (dllexport) 

以 [appdomain](../../cpp/appdomain.md)修飾詞標記的函式 **`__declspec`** 會編譯為 MSIL (不是原生) ，而且 managed 函式不支援 ([匯出](../../windows/attributes/export.md)修飾詞) 的匯出資料表 **`__declspec`** 。

您可以宣告 Managed 函式具有公用的存取範圍。 如需詳細資訊，請參閱 [類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 和 [成員可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。

C4394 一律會發出錯誤。  您可以使用或/wd 關閉此警告 `#pragma warning` ; **/wd**如需詳細資訊，請參閱[warning](../../preprocessor/warning.md)或[/W、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3](../../build/reference/compiler-option-warning-level.md) 、/W4、/Wall、/wd、/we、/wo、/Wv、、、、、/wx (警告層級) 。

## <a name="example"></a>範例

下列範例會產生 C4394。

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
