---
title: 位址的儲存 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d892aac81efa8c2628c8662558b52cc1eb2e21c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="storage-of-addresses"></a>位址的儲存
位址所需的儲存數量和位址的意義取決於編譯器的實作。 不同類型的指標不一定會具有相同長度。 因此，**sizeof(char \*)** 不一定等於 **sizeof(int \*)**。  
  
 **Microsoft 特定的**  
  
 對於 Microsoft C 編譯器，**sizeof(char \*)** 等於 **sizeof(int \*)**。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [指標宣告](../c-language/pointer-declarations.md)