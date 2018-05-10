---
title: register 儲存類別指定名稱 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 211f623923286e598f495920bcbdac3a9321b13a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="register-storage-class-specifier"></a>register 儲存類別指定名稱
**Microsoft 特定的**  
  
 Microsoft C/C++ 編譯器不接受使用者要求的暫存器變數。 不過，為了提供可攜性，編譯器接受其他所有與 **register** 關鍵字相關的語意。 例如，您不能對暫存器物件套用一元傳址運算子 (**&**)，也無法在陣列上使用 **register** 關鍵字。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [內部層級宣告的儲存類別規範](../c-language/storage-class-specifiers-for-internal-level-declarations.md)