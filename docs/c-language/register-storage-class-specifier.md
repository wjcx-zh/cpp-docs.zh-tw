---
title: "register 儲存類別指定名稱 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95c06471b7d8ea60754c29a9bde3159174e9c194
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="register-storage-class-specifier"></a>register 儲存類別指定名稱
**Microsoft 特定的**  
  
 Microsoft C/C++ 編譯器不接受使用者要求的暫存器變數。 不過，為了提供可攜性，編譯器接受其他所有與 **register** 關鍵字相關的語意。 例如，您不能對暫存器物件套用一元傳址運算子 (**&**)，也無法在陣列上使用 **register** 關鍵字。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內部層級宣告的儲存類別規範](../c-language/storage-class-specifiers-for-internal-level-declarations.md)