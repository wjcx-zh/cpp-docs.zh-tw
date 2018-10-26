---
title: alloc_text | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs:
- C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d131cee2194ba139fdb99d9c0fa7ae2c922fe84d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073809"
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

**Alloc_text** pragma 不會處理 c + + 成員函式 」 或 「 多載函式。 它是僅適用使用 C 連結宣告的函式 — 也就是宣告的函式與**extern"C"** 連結規格。 如果您嘗試在使用 C++ 連結的函式上使用這個 pragma，則會產生編譯器錯誤。

因為函式定址使用`__based`不支援，指定區段位置需要使用**alloc_text** pragma。 所指定的名稱*textsection*應該用雙引號括住。

**Alloc_text** pragma 必須出現在任何指定的函式和這些函式定義之前宣告之後。

中所參考的函式**alloc_text** pragma 應該與 pragma 相同的模組中定義。 如果沒有這樣做，而且之後將未定義的函式編譯為不同的文字區段，則不一定會攔截錯誤。 雖然程式通常會正確執行，但是函式不會配置在預定的區段中。

其他限制**alloc_text**如下所示：

- 不能在函式內部使用。

- 使用時機必須是在函式宣告之後，但是在函式定義之前。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)