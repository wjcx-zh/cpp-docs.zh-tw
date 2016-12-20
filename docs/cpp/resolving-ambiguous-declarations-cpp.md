---
title: "語意模糊解決 | Microsoft Docs"
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
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 語意模糊解決
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要從一個類型明確轉換成另一個類型，您必須使用轉型來指定所需的類型名稱。  某些類型轉換會導致語意模稜兩可的情況。  下列函式樣式類型轉換就是模稜兩可的情況：  
  
```  
char *aName( String( s ) );  
```  
  
 究竟是使用函式樣式轉型做為初始設定式的函式宣告或是物件宣告並不明確：它可以宣告傳回採用一個 `String` 類型引數之 **char \*** 類型的函式，也可以宣告 `aName` 物件並將它初始化，其中 `s` 值會轉型為 `String` 類型。  
  
 如果宣告可以視為有效的函式宣告，則會以此方式處理。  只有在不可能是函式宣告的情況下 \(也就是它的語意不正確\)，才會查看陳述式是否為函式樣式類型轉換。  因此，編譯器會將陳述式視為函式宣告，必且忽略識別項 `s` 前後的括號。  換句話說，陳述式：  
  
```  
char *aName( (String)s );  
```  
  
 和  
  
```  
char *aName = String( s );  
```  
  
 很明確就是物件的宣告，而且會叫用從 `String` 類型到 **char \*** 類型的使用者定義轉換來初始化 `aName`。  
  
## 請參閱  
 [C\+\+ Abstract Declarators](http://msdn.microsoft.com/zh-tw/e7e18c18-0cad-4450-942b-d27e1d4dd088)