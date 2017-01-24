---
title: "marshal_context 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 類別 [C++]"
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個類別會在原生和 Managed 環境之間轉換。  
  
## 語法  
  
```  
class marshal_context  
```  
  
## 備註  
 為需要內容的轉換資料時使用 `marshal_context` 類別。  如需轉換需要內容，以及詳細資訊的封送處理檔案必須包含 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md) 的參考。  封送處理的結果，當您使用內容時有效，只有在終結 `marshal_context` 物件。  若要儲存結果，您必須複製資料。  
  
 相同 `marshal_context` 來多資料轉換。  重複使用內容將不會影響從先前封送處理呼叫的結果。  
  
## 需求  
 **標頭檔:** \<msclr\\marshal.h\>、\<msclr\\ marshal\_windows.h\>、\<msclr\\ marshal\_cppstd.h\> 或 \<msclr\\ marshal\_atl.h\>  
  
 **命名空間:** msclr::interop  
  
## 請參閱  
 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)