---
title: alloc_text
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 399e8956a511f289b480e66db7f03cac0a6c7c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389355"
---
# <a name="alloctext"></a>alloc_text
為要放置指定之函式定義的程式碼區段命名。 pragma 必須在函式宣告子與具名函式的函式定義之間發生。

## <a name="syntax"></a>語法

```
#pragma alloc_text( "
textsection
", function1, ... )
```

## <a name="remarks"></a>備註

**Alloc_text** pragma 不會處理C++成員函式 」 或 「 多載函式。 它是僅適用使用 C 連結宣告的函式 — 也就是宣告的函式與**extern"C"** 連結規格。 如果您嘗試在使用 C++ 連結的函式上使用這個 pragma，則會產生編譯器錯誤。

因為函式定址使用`__based`不支援，指定區段位置需要使用**alloc_text** pragma。 所指定的名稱*textsection*應該用雙引號括住。

**Alloc_text** pragma 必須出現在任何指定的函式和這些函式定義之前宣告之後。

中所參考的函式**alloc_text** pragma 應該與 pragma 相同的模組中定義。 如果沒有這樣做，而且之後將未定義的函式編譯為不同的文字區段，則不一定會攔截錯誤。 雖然程式通常會正確執行，但是函式不會配置在預定的區段中。

其他限制**alloc_text**如下所示：

- 不能在函式內部使用。

- 使用時機必須是在函式宣告之後，但是在函式定義之前。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)