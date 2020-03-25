---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8164f47190267627bdaf7c7ee2f03f22f65c8f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161057"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 專屬**

**__Declspec**擴充屬性，可用於函數的宣告。

## <a name="syntax"></a>語法

> 傳回*類型*__declspec （nothrow） [*呼叫慣例*] 函*式名稱*（[*引數清單*]）

## <a name="remarks"></a>備註

我們建議所有新的程式碼都使用[noexcept](noexcept-cpp.md)運算子，而不是 `__declspec(nothrow)`。

這個屬性會告知編譯器其所呼叫的已宣告函式絕對不會擲回例外狀況。 不過，它不會強制執行指示詞。 換句話說，它絕對不會導致叫用[std：： terminate](../standard-library/exception-functions.md#terminate) ，與 `noexcept`不同，或在**std： c + + 17**模式（Visual Studio 2017 15.5 版和更新版本）中 `throw()`。

使用同步例外狀況處理模型時 (現在為預設值)，編譯器可以排除在這類函式中追蹤某些無法還原物件存留期的機制，並大幅降低程式碼大小。 假設有下列的預處理器指示詞，下列三個函式宣告在 **/std： c + + 14**模式中是相等的：

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

在 **/std： c + + 17**模式中，`throw()` 不等於使用 `__declspec(nothrow)` 的其他專案，因為如果函式擲回例外狀況，則會導致叫用 `std::terminate`。

`void __stdcall f3() throw();` 宣告會使用C++標準所定義的語法。 在 c + + 17 中，`throw()` 關鍵字已被取代。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
