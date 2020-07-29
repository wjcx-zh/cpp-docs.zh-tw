---
title: alloc_text pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: c638c2026a493453aeb5aff00ba6273efb5f184e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219439"
---
# <a name="alloc_text-pragma"></a>alloc_text pragma

為要放置指定之函式定義的程式碼區段命名。 pragma 必須在函式宣告子與具名函式的函式定義之間發生。

## <a name="syntax"></a>語法

> **#pragma alloc_text （** "*textsection*" **，** *function1* [**，** *function2* ...] **）**

## <a name="remarks"></a>備註

**Alloc_text** pragma 不會處理 c + + 成員函式或多載函式。 它僅適用于使用 C 連結宣告的函式，也就是以**extern "C"** 連結規格宣告的函式。 如果您嘗試在使用 C++ 連結的函式上使用這個 pragma，則會產生編譯器錯誤。

由於不支援使用的函數定址 **`__based`** ，因此指定區段位置需要使用**alloc_text** pragma。 *Textsection*所指定的名稱應該以雙引號括住。

**Alloc_text** pragma 必須出現在任何指定函數的宣告之後，以及這些函式的定義之前。

**Alloc_text** pragma 中參考的函式應該在與 pragma 相同的模組中定義。 否則，如果未定義的函式稍後編譯成不同的文字區段，則不一定會攔截到此錯誤。 雖然程式通常會正確執行，但是函式不會配置在預定的區段中。

**Alloc_text**的其他限制如下：

- 不能在函式內使用。

- 使用時機必須是在函式宣告之後，但是在函式定義之前。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞與 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
