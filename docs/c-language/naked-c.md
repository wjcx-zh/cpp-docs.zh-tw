---
title: Naked (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6665bafb0041989e99a3a766204555f969d16c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062146"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft 專屬**

naked 儲存類別屬性是 Microsoft 專有的 C 語言擴充功能。 編譯器會針對以 naked 儲存類別屬性宣告的函式，產生不具初構和終解程式碼的程式碼。 當您需要使用內嵌組合語言程式碼撰寫自己的初構/終解程式碼序列時，naked 函式會很有用。 naked 函式在撰寫虛擬裝置驅動程式方面也很實用。

如需使用 naked 屬性的特定資訊，請參閱 [Naked 函式](../c-language/naked-functions.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)