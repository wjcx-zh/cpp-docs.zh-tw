---
title: nothrow （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 01/03/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69a706577cf112c3d8a3b7748f72679f7213936d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420646"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 特定的**

可在函式的宣告中使用的 `__declspec` 擴充屬性。

## <a name="syntax"></a>語法  
  
> *傳回型別*__declspec （nothrow) [*呼叫慣例*]*函式名稱*([*引數清單*])

## <a name="remarks"></a>備註

我們建議所有新的程式碼使用[noexcept](noexcept-cpp.md)運算子而不是`__declspec(nothrow)`。

這個屬性會告知編譯器其所呼叫的已宣告函式絕對不會擲回例外狀況。 不過，它不會強制執行指示詞。 換句話說，它永遠不會造成[std:: terminate](../standard-library/exception-functions.md#terminate)叫用時，不像`noexcept`，或在**std:c + + 17**模式 (Visual Studio 2017 15.5 和更新版本)， `throw()`。

使用同步例外狀況處理模型時 (現在為預設值)，編譯器可以排除在這類函式中追蹤某些無法還原物件存留期的機制，並大幅降低程式碼大小。 指定下列前置處理器指示詞，以下三個函式宣告相當於 **/std:c + + 14**模式：

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

在 **/std:c + + 17**模式中，`throw()`不等同於其他使用`__declspec(nothrow)`因為這會導致`std::terminate`從函式擲回的例外狀況時要叫用。

`void __stdcall f3() throw();`宣告會使用 c + + 標準所定義的語法。 在 C + + 17`throw()`關鍵字已被取代。

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)  
[noexcept](noexcept-cpp.md)  
[關鍵字](../cpp/keywords-cpp.md)  
