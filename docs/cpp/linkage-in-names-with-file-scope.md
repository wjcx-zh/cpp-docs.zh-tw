---
title: "具有檔案範圍的名稱連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- static modifier, file scope
- static names and file scope
- file scope [C++]
- declarations [C++], external
- external linkage, scope linkage rules
- static variables, external declarations
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c4d33071426eac428cc1728aa13b403953a99389
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="linkage-in-names-with-file-scope"></a>檔案範圍的名稱連結
下列連結規則適用於具有檔案範圍的名稱 (除了 `typedef` 和列舉程式名稱以外)：  
  
-   如果名稱明確宣告為**靜態**，它具有內部連結，並識別本身所屬轉譯單位內的程式項目。  
  
-   列舉程式名稱和 `typedef` 名稱沒有連結。  
  
-   具有檔案範圍的所有其他名稱都具有外部連結。  
  
 **Microsoft 特定的**  
  
-   如果具有檔案範圍的函式名稱明確宣告為**內嵌**，其具有外部連結，如果具現化，或參考其位址。 因此，具有檔案範圍的函式可以有內部或外部連結。  
  
 **END Microsoft 特定的**  
  
 若下列條件成立，類別會有內部連結：  
  
-   類別使用 C++ 功能 (例如，成員存取控制、成員函式、建構函式、解構函式等)。  
  
-   類別未在具有外部連結的另一個名稱宣告中使用。 這個條件約束表示，若將類別類型的物件傳遞至具有外部連結的函式，會造成類別擁有外部連結。  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)
