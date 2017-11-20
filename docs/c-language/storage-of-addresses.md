---
title: "位址的儲存 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d0e996ac191ba3091925a85937e7636a2425215
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-addresses"></a>位址的儲存
位址所需的儲存數量和位址的意義取決於編譯器的實作。 不同類型的指標不一定會具有相同長度。 因此，**sizeof(char \*)** 不一定等於 **sizeof(int \*)**。  
  
 **Microsoft 特定的**  
  
 對於 Microsoft C 編譯器，**sizeof(char \*)** 等於 **sizeof(int \*)**。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [指標宣告](../c-language/pointer-declarations.md)