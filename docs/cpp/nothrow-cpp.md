---
title: nothrow （c + +） |Microsoft Docs
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
ms.openlocfilehash: 0261ed9d1e84849f408c3d764693cb95ac7019d2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408062"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 專屬**

A **__declspec**可用的函式宣告中的擴充的屬性。

## <a name="syntax"></a>語法  
  
> *傳回型別*__declspec （nothrow) [*呼叫慣例*]*函式名稱*([*引數清單*])

## <a name="remarks"></a>備註

我們建議所有新的程式碼[noexcept](noexcept-cpp.md)運算子而非`__declspec(nothrow)`。

這個屬性會告知編譯器其所呼叫的已宣告函式絕對不會擲回例外狀況。 不過，它不會強制指示詞。 換句話說，它永遠不會造成[std:: terminate](../standard-library/exception-functions.md#terminate)要叫用，不像`noexcept`，或是在 **/std: c + + 17**模式 (Visual Studio 2017 15.5 版和更新版本)， `throw()`。

使用同步例外狀況處理模型時 (現在為預設值)，編譯器可以排除在這類函式中追蹤某些無法還原物件存留期的機制，並大幅降低程式碼大小。 指定下列前置處理器指示詞，下方的三個函式宣告相等 **/std: c + + 14**模式︰

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

在 **/std: c + + 17**模式中，`throw()`不等同於使用其他`__declspec(nothrow)`因為這會導致`std::terminate`從函式擲回的例外狀況時要叫用。

`void __stdcall f3() throw();`宣告會使用 c + + 標準所定義的語法。 在 C + + 17`throw()`關鍵字已被取代。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱
 [__declspec](../cpp/declspec.md)  
 [noexcept](noexcept-cpp.md)  
 [關鍵字](../cpp/keywords-cpp.md)  