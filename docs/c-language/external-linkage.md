---
title: "外部連結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "外部連結"
  - "外部連結, 關於外部連結"
  - "連結 [C++], 外部"
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 外部連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果識別項在檔案範圍層級的第一個宣告未使用 **static** 儲存類別規範，則物件會具有外部連結。  
  
 如果函式的識別項宣告沒有 *storage\-class\-specifier*，其連結的判斷方式會像是使用 *storage\-class\-specifier* `extern` 宣告一般。  如果物件的識別項宣告具有檔案範圍，但沒有 *storage\-class\-specifier*，表示其連結為外部。  
  
 具有外部連結的識別項名稱所指定的函式或資料物件，會與任何其他具有外部連結的相同名稱宣告所指定的函式或資料物件相同。  這兩種宣告可以位於相同轉譯單位或不同轉譯單位中。  如果物件或函式同時具有全域存留期，則物件或函式會由整個程式共用。  
  
## 請參閱  
 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)