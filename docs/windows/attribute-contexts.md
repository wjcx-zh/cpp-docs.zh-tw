---
title: "Attribute Contexts | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], contexts"
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Attribute Contexts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C \+ \+ 屬性可以使用四個基本的欄位來說明： 它們可以套用到目標 \(**套用至**\)，如果不是可重複 \(**重複**\)、 所需的其他屬性的目前狀態 \(**必要屬性**\)，並以其他屬性不相容的情形 \(**無效的屬性**\)。  這些欄位是以每個屬性的參考主題中的表格所示。  這些欄位的描述如下。  
  
## 適用於  
 此欄位描述是合法的目標，指定屬性的不同 C\+\+ 語言項目。  舉個例說，如果屬性會指定 「 類別 」，在**套用至**欄位，這會指示屬性只能套用到合法的 C\+\+ 類別。  如果將屬性套用至類別的成員函式，將產生一個語法錯誤。  
  
 如需詳細資訊，請參閱[屬性的用法](../windows/attributes-by-usage.md)。  
  
## 可重複  
 這個欄位會指出是否可以設為相同的目標重複套用屬性。  大部分的屬性不是可重複的。  
  
## 必要的屬性  
 這個欄位會列出所需用到的其他屬性指定的屬性，才能正確運作的禮物 \(亦即，套用至同一個目標\)。  很常見的屬性，若要讓這個欄位的任何項目。  
  
## 無效的屬性  
 這個欄位會列出與指定的屬性不相容的其他屬性。  很常見的屬性，若要讓這個欄位的任何項目。  
  
## 請參閱  
 [C\+\+ Attributes Reference](../windows/cpp-attributes-reference.md)