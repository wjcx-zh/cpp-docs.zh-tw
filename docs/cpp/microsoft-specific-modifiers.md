---
title: Microsoft 特定修飾詞
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2f56220ba15027a522264b91366cab9cf0b65d21
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506537"
---
# <a name="microsoft-specific-modifiers"></a>Microsoft 特定修飾詞

本節將描述下列各層面 Microsoft 專有的 C++ 擴充功能：

- [根據定址](based-addressing.md)，使用指標作為基底的做法，可從中位移其他指標

- [函式呼叫慣例](calling-conventions.md)

- 使用 [__declspec](declspec.md) 關鍵字宣告的擴充儲存類別屬性

- [__W64](w64.md)關鍵字

## <a name="microsoft-specific-keywords"></a>Microsoft 專有的關鍵字

許多 Microsoft 專有關鍵字可用來將宣告子修改為衍生類型。 如需宣告子的詳細資訊， [請參閱宣告](./declarations-and-definitions-cpp.md)子。

|關鍵字|意義|是否用來形成衍生類型？|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|後面的名稱會將 32 位元位移宣告為宣告中包含的 32 位元基底。|是|
|[__cdecl](cdecl.md)|後面的名稱會使用 C 命名和呼叫慣例。|是|
|[__declspec](declspec.md)|後面的名稱會指定 Microsoft 專有的儲存類別屬性。|否|
|[__fastcall](fastcall.md)|後面的名稱會將函式宣告為使用暫存器 (如果有的話)，而不使用可進行引數傳遞的堆疊。|是|
|[__restrict](extension-restrict.md)|類似于 __declspec ([限制](restrict.md)) ，但用於變數。|否|
|[__stdcall](stdcall.md)|後面的名稱會指定採用標準呼叫慣例的函式。|是|
|[__w64](w64.md)|在 64 位元編譯器上將資料類型標示為較大。|否|
|[__unaligned](unaligned.md)|指出某個類型或其他資料的指標未對齊。|否|
|[__vectorcall](vectorcall.md)|後面的名稱會將函式宣告為只要有暫存器可用即使用暫存器 (包括 SSE 暫存器)，而不使用可進行引數傳遞的堆疊。|是|

## <a name="see-also"></a>另請參閱

[C + + 語言參考](cpp-language-reference.md)
