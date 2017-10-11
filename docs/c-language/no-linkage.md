---
title: "無連結 | Microsoft Docs"
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
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 278325c1ad1b31ce20b6a17034be5e4731f6da78
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="no-linkage"></a>無連結
如果區塊中某個識別項的宣告並未包含 `extern` 儲存類別指定名稱，則不會連結識別項，且該識別項在函式中是唯一的。  
  
 下列識別項不會進行連結：  
  
-   除了物件或函式之外，可項識別項宣告為任何項目  
  
-   宣告為函式參數的識別項  
  
-   已宣告不含 `extern` 儲存類別指定名稱之物件的區塊範圍識別項  
  
 如果識別項未連結，則在相同範圍層級中再次宣告相同名稱 (在宣告子或類型指定名稱中) 會產生符號重新定義錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
