---
title: Naked (C) | Microsoft Docs
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
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 2aa9ba1d3e6397a35389c2ee46ab30f19c0e6227
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="naked-c"></a>Naked (C)
**Microsoft 特定的**  
  
 naked 儲存類別屬性是 Microsoft 專有的 C 語言擴充功能。 編譯器會針對以 naked 儲存類別屬性宣告的函式，產生不具初構和終解程式碼的程式碼。 當您需要使用內嵌組合語言程式碼撰寫自己的初構/終解程式碼序列時，naked 函式會很有用。 naked 函式在撰寫虛擬裝置驅動程式方面也很實用。  
  
 如需使用 naked 屬性的特定資訊，請參閱 [Naked 函式](../c-language/naked-functions.md)。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)
