---
title: Based 指標 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79e515a3f108d0857d2f8860566e14ee0acdefe3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097571"
---
# <a name="based-pointers-c"></a>Based 指標 (C)

**Microsoft 專屬**

[__based (C++ 參考)](../cpp/based-pointers-cpp.md)

對於 Microsoft 32 位元和 64 位元 C 編譯器，基底指標是來自 32 位元或 64 位元指標基底的 32 位元或 64 位元位移。 基底定址在精確控制配置物件的區段時很實用，可藉此縮減可執行檔的大小及加快執行速度。 一般而言，指定基底指標的形式為

> *type* **__based(** *base* **)** *declarator*

基底定址的「基底指標」變數可讓您將指標指定為基底。 然後基底指標就是進入記憶體區段內的位移，從做為基底之指標的開頭開始。 以指標位址為基礎的指標是 `__based` 關鍵字在 32 位元和 64 位元編譯中有效的唯一形式。 在這類編譯中，它們是從 32 位元或 64 位元基底的 32 位元或 64 位元位移。

以指標為基礎之指標的其中一項用途，就是包含指標的持續性識別項。 以指標為基礎的指標所組成的連結清單可以儲存至磁碟，然後以仍然有效的指標重新載入至記憶體中的另一個位置。

下列範例將示範以指標為基礎的指標。

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

為指標 `vpBuffer` 所指派的記憶體位址，會在程式稍後的位置中進行配置。 連結清單會重新配置相對於 `vpBuffer` 的值。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)