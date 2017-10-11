---
title: "命名空間 | Microsoft Docs"
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
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ba0a5fcce92c0d8afe19e3b98d2ba20e1d22d6a4
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="name-spaces"></a>命名空間
編譯器會設定「命名空間」以區別不同類型的項目所使用的識別項。 每個命名空間內的名稱都必須是唯一的，才能避免衝突發生，但是相同的名稱可能會出現在多個命名空間中。 這表示，假設項目位於不同的命名空間中，您可以將同一個識別項用於兩個或多個不同的項目。 編譯器可以根據程式中識別項的語法內容解析參考。  
  
> [!NOTE]
>  請勿混淆有限的 C 命名空間概念與 C++ "namespace" 功能。 如需詳細資訊，請參閱《C++ 語言參考》中的[命名空間](../cpp/namespaces-cpp.md)。  
  
 這個清單將描述 C 中使用的命名空間。  
  
 陳述式標籤  
 具名陳述式標籤是陳述式的一部分。 陳述式標籤的定義後面一律接著一個冒號，但它不屬於 **case** 標籤的一部分。 陳述式標籤一律緊接在關鍵字 `goto` 後面使用。 陳述式標籤不需要與其他名稱或其他函式中的標籤名稱不同。  
  
 結構、等位和列舉標記  
 這些標記是結構、等位和列舉類型規範的一部分，如果存在的話，一律緊接在保留字 `struct`、**union** 或 `enum` 的後面。 標記名稱必須與具有相同可視性的所有其他結構、列舉或等位標記有所區別。  
  
 結構或等位的成員  
 成員名稱會在與每個結構和等位類型相關聯的命名空間中配置。 也就是說，同一個識別項可以同時是任意數目的結構或等位中的元件名稱。 元件名稱的定義一律在結構或等位型別規範內發生。 元件名稱一律緊接在成員選取運算子 (**->** 和 **.**) 的後面。 成員名稱在結構或等位內必須是唯一的，但是不需要與程式中的其他名稱不同，包括不同結構和等位之成員的名稱，或結構本身的名稱。  
  
 一般識別項  
 所有其他名稱都屬於包括變數、函式 (包括正式參數和區域變數) 和列舉常數在內的命名空間。 識別項名稱具有巢狀可視性，因此您可以在區塊內重新定義這些名稱。  
  
 Typedef 名稱  
 Typedef 名稱不可做為相同範圍中的識別項使用。  
  
 例如，由於結構標記、結構成員和變數名稱分別位於三個不同的命名空間中，因此這個範例中三個名為 `student` 的項目互不衝突。 每個項目的內容都可正確解譯程式中出現的每一個 `student`  (如需結構的資訊，請參閱[結構宣告](../c-language/structure-declarations.md))。  
  
```  
struct student {  
   char student[20];  
   int class;  
   int id;  
   } student;  
```  
  
 當 `student` 出現在 `struct` 關鍵字後面時，編譯器會將它辨識為結構標記。 當 `student` 出現在成員選取運算子 (**->** 或 **.**) 後面時，名稱會參考結構成員。 在其他內容中，`student` 會參考結構變數。 不過，不建議多載標記命名空間，因為它使意義含糊不清。  
  
## <a name="see-also"></a>另請參閱  
 [程式結構](../c-language/program-structure.md)
