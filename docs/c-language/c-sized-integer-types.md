---
title: "C 大小整數類型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: db04c6862be26d5641a485c47ac7fd71b43d16fe
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="c-sized-integer-types"></a>C 大小整數類型
**Microsoft 特定的**  
  
 Microsoft C 的功能支援可調整大小的整數類型。 您可以使用 __int*n* 類型指定名稱來宣告 8、16、32 或 64 位元的整數變數，其中 *n* 是整數變數的大小 (以位元為單位)。 *n* 的值可以是 8、16、32 或 64。 下列範例宣告了四種可調整大小整數類型的變數：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 前三類可調整大小的整數與具有相同大小的 ANSI 類型同義，且當撰寫可移植程式碼的行為模式在多個平台上完全相同時，這也會很有用。 請注意，__int8 資料類型與 char 類型同義，\__int16 與 short 類型同義，而 \__int32 與 int 類型同義。 \__int64 類型沒有對等的 ANSI 對應項目。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)
