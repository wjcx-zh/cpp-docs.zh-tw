---
title: 類型 char | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec964d9b81ee93f888bbd4152f06f6bdf51b6d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053826"
---
# <a name="type-char"></a>類型 char

`char` 類型可用來儲存可顯示字元集之成員的整數值。 該整數值是對應所指定字元的 ASCII 碼。

**Microsoft 專屬**

`unsigned char` 類型的字元值範圍是十六進位的 0 到 0xFF。 **signed char** 的範圍是 0x80 到 0x7F。 這些範圍會分別轉譯為十進位的 0 到 255 及十進位的 -128 到 +127。 /J 編譯器選項將預設值從 **signed** 變更為 `unsigned`。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[基本類型的儲存體](../c-language/storage-of-basic-types.md)