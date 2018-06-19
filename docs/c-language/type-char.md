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
ms.openlocfilehash: 9b4db02292398da5c35f2894d4ce278cea88a584
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386825"
---
# <a name="type-char"></a>類型 char
`char` 類型可用來儲存可顯示字元集之成員的整數值。 該整數值是對應所指定字元的 ASCII 碼。  
  
 **Microsoft 特定的**  
  
 `unsigned char` 類型的字元值範圍是十六進位的 0 到 0xFF。 **signed char** 的範圍是 0x80 到 0x7F。 這些範圍會分別轉譯為十進位的 0 到 255 及十進位的 -128 到 +127。 /J 編譯器選項將預設值從 **signed** 變更為 `unsigned`。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)